# 既存の UIKit のプロジェクトで SwiftUI を導入する
<!-- TOC -->

- [既存の UIKit のプロジェクトで SwiftUI を導入する](#既存の-uikit-のプロジェクトで-swiftui-を導入する)
  - [概要/目的](#概要目的)
  - [SwiftUI でのクリーンアーキテクチャ](#swiftui-でのクリーンアーキテクチャ)
    - [Presentation 層](#presentation-層)
      - [View](#view)
      - [Presentation](#presentation)
    - [Business Logic 層](#business-logic-層)
      - [RepositoryProtocol](#repositoryprotocol)
      - [Interactor](#interactor)
      - [State](#state)
      - [Entity](#entity)
    - [Data Access](#data-access)
      - [Repository](#repository)
  - [UIKit のプロジェクトに SwiftUI を導入する](#uikit-のプロジェクトに-swiftui-を導入する)
    - [Swift Package Manager](#swift-package-manager)
    - [UIViewController / UIHostingControler](#uiviewcontroller--uihostingcontroler)

<!-- /TOC -->
## 概要/目的

- UIKit で作られた既存プロジェクトに SwiftUI を導入する
- FatViewController になっている設計を今後の SwiftUI への完全移行をみすえてクリーンな設計にする

## SwiftUI でのクリーンアーキテクチャ

![SwiftUI Architecture](images/SwiftUI-in-UIKit/SwiftUI%20Project%20Architecture%201.jpg)

### Presentation 層

#### View

- SwiftUI View
- State の変更に応じた UI を表示する
- ユーザーのアクションを受け取り、Interactor や Presentation に伝達する
- @EnvironmentObject を使う
  - Dependency Injection が可能
    - // TODO: イニシャライザでやってもいいけど、@EnvironmentObject を使う理由は？
  - 子・孫 View でも使える

```swift
import SwiftUI

struct ContentView: View {
    @EnvironmentObject private var interactor: Interactor
    @EnvironmentObject private var presentation: Presentation

    var body: some View {
        ZStack {
            Color(.secondary)

            Text("Hello, World!").padding()

            if let state = presentation.sheetState {
                state.content
                    .transition(.opacity.animation(.easeInOut))
            }
        }
        .onAppear(perform: interactor.fetch)
    }
```

#### Presentation

- ObservableObject もしくは @State
- 画面の遷移を管理する
  - (iOS 13) iOS14.0+ `.onChange(of:perform:)` を使わずに、Presentation を監視する
- (VIPER でいうところの Router？)

```swift
import SwiftUI

class Presentation: ObservableObject {
    enum SheetState {
        case loading
        case detail(entity: Entity)

        @ViewBuilder
        var content: some View {
            switch self {
            case .loading:
                IndicatorView()
            case .detail(let entity):
                DetailView(entity: entity)
            }
        }
    }

    @Published var sheetState: SheetState? = .none
    @Published var completed: Bool = false
}
```

### Business Logic 層

#### RepositoryProtocol

- protocol
- 依存性逆転の原則 に基づき、Repository を抽象化する

```swift
import Foundation
import Combine

protocol RepositoryProtocol {
    func fetch() -> AnyPublisher<[Entity], Error>
    func create(with parameter: Parameter) -> AnyPublisher<Entity, Error>
}
```

#### Interactor

- ObservableObject
- State と Repository に依存する
  - Repository は protocol を介することで、抽象に依存する

```swift
import Foundation
import Combine

class Interactor: ObservableObject {
    @Published var state: State
    let repository: RepositoryProtocol

    private var cancellables: Set<AnyCancellable> = []

    init(repository: RepositoryProtocol) {
        self.repository = repository
        self.state = .init()
    }

    func fetch() {
        repository.fetch()
            .receive(on: DispatchQueue.main)
            .sink { [weak self] in self?.state.datasource = $0 }
            .store(in: &cancellables)
    }

    func toggleSelected(id: Entity.ID) {
        if state.selections.contains(id) {
            state.selections.remove(id)
        } else {
            state.selections.insert(id)
        }
    }
}
```

#### State

- SwiftUI View で表示する State を管理する
- Interactor によって更新される or @Binding によって View で更新される

```swift
import Foundation

struct State {
    var datasource: [String: [Entity]]
    var selections: Set<Entity.ID> = []
}
```

#### Entity

- 構造体
- 全ての層で Entity を使うことを許容する

```swift
import Foundation

struct Entity: Codable, Identifiable {
    typealias ID = String
    var id: ID
}
```

### Data Access

#### Repository

- Database を使った永続化や API との通信を行う
- RepositoryProtocol に適合した MockRepository を作成しておくことで
  - Preview での確認ができる

```swift
struct MockRepository: RepositoryProtocol {
    func fetch() -> AnyPublisher<[Entity], Error> {
        let response: [Entity] = [.init(id: "foo"), .init(id: "bar"), .init(id: "baz")]
        Future { promise in
            promise(.success(response))
            // promise(.failure(APIServerError.badServerResponse))
        }
        .eraseToAnyPublisher()
    }

    func create(with parameter: Parameter) -> AnyPublisher<Entity, Error> {
        Future { promise in
            promise(.success(Entity(id: "created")))
            // promise(.failure(APIServerError.badServerResponse))
        }
        .eraseToAnyPublisher()
    }
}
```

## UIKit のプロジェクトに SwiftUI を導入する

![SwiftUI in UIKit Architecture](images/SwiftUI-in-UIKit/SwiftUI%20Project%20Architecture%202.jpg)

### Swift Package Manager

- Presentation 層 と Business Logic 層 を SPM を使って モジュール化する
  - Preview 時のビルド対象を SwiftUI View に関わるプログラムだけにする
- Main module から参照できるようにアクセス修飾子を変更する
  - struct, class を public にする
  - イニシャライザ を public にする
  - 参照したいプロパティを public にする

### UIViewController / UIHostingControler

- SwiftUI View を呼び出す
- Repository, Interactor, Presentation を作成し View に渡す
- State を監視し、変更に応じて処理を行う
- Container View を使うことで画面の一部だけを SwiftUI に置き換えることも可能

```swift
import Combine
import SwiftUI
import UIKit

import ViewModule

final class ViewController: UIViewController {
    struct Dependency {
        var repository: RepositoryProtocol
    }

    private var dependency: Dependency
    private var cancellables: Set<AnyCancellable> = []
    @IBOutlet private var containerView: UIView!

    init?(coder: NSCoder, dependency: Dependency) {
        self.dependency = dependency
        super.init(coder: coder)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        let interactor = Interactor(repository: dependency.repository)
        let presentation = Presentation()
        let rootView = ContentView()
            .environmentObject(interactor)
            .environmentObject(presentation)
        let viewController = UIHostingController(rootView: rootView)

        addChild(viewController)
        viewController.view.frame = self.containerView.bounds
        viewController.view.autoresizingMask = [.flexibleHeight, .flexibleWidth]
        self.containerView.addSubview(viewController.view)
        viewController.didMove(toParent: self)

        presentation.$completed
            .sink { [weak self] in if $0 { self?.dismiss(animated: true) } }
            .store(in: &self.cancellables)
    }
}

```
