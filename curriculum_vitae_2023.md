# 職務経歴書

## 経歴

### ARS 株式会社（2014/04 - 2017/09）
| 担当 | 業務内容 |
| --- | --- |
| システムエンジニア | 大手銀行の信用管理システムの詳細設計 ~ テスト<br>金融機関向けの人事・ワークフローシステムの要件定義 ~ 運用 |

### 株式会社 ietty（2017/10 - 現在）
| 担当 | 業務内容 |
| --- | --- |
| リードエンジニア | チャット型不動産賃貸サービス ietty の施策企画・設計・開発 |

| 年 | 内容 | 担当領域 |
| --- | --- | --- |
| 2017 | サーバーサイド・Chrome Extension の開発を担当 | サーバーサイド |
| 2018 | 体制変更のため、iOS アプリをメインとしてアプリとサーバーサイドの開発を担当<br>CI/CD・SwiftUI の導入などを通して、iOS エンジニア以外も開発を行える環境を整備 | iOSアプリ・サーバーサイド |
| 2021 | エンジニア主導の施策企画と検証ができる体制を提案・構築<br>1チームの施策立案・実装と全体マネジメントを担当<br>Firebase Analytics・RemoteConfig を導入し、施策効果を計測できる環境を整備 | 開発チームリード・企画・iOS・サーバーサイド |
| 2022 | Android アプリを WebView ベースからネイティブ対応するため Android 開発を担当<br>限定された機能を短工期で実装するために Jetpack Compose で開発 | Android・iOS・サーバーサイド |

## スキル・経験の詳細

### iOS
#### できること
  - Swift を使ったアプリ開発
    - UIKit・SwiftUI を使った UI 構築
    - [UIKit ベースのアプリへの SwiftUI 導入](https://hira22.github.io/Articles/既存のUIKitのプロジェクトにSwiftUIを導入する.html)
    - Combine の導入・Concurrency への移行
  - テストがしやすい設計と XCTest を使ったユニットテストの実装
    - [テストと XCTest](https://hira22.github.io/Articles/XCTest.html)
    - [リファクタリングと設計の基本](https://hira22.github.io/Articles/リファクタリングの話.html)
  - 通知・VoIP・Share Extension 機能実装
  - Bitrise での CI/CD 構築
  - 周辺業務（Store への申請、証明書の作成、テストアプリの配信）

#### 業務経験がないこと
  - Objective-C
  - RxSwift
  - iPad 対応
  - Bluetooth・Audio（動画）・位置情報・Share 以外の Extension

### Android
#### できること
  - Kotlin を使ったアプリ開発
    - Jetpack Compose を使った UI 構築
    - [Jetpack Compose を生かした設計](https://www.figma.com/file/lfTRK58MdKPsIKUFmswC8q/Jetpack-Compose-%E8%A8%AD%E8%A8%88?node-id=0%3A1&t=Sm8hlgUfGhzxUvMn-1)
    - Ktor Client を使った通信
    - Coroutine を使った非同期処理の実装
    - WebView の制御

#### 業務経験がないこと
  - View を使った UI 構築
  - Jetpack ViewModel を使った MVVM アークテクチャの実装
  - Hilt や Koin などのDIライブラリを使った実装

### Firebase
#### できること
  - Analytics のイベント名・イベントパラメータ・トリガーの設計
  - iOS・Android アプリへの Analytics コードの設計・実装
  - Remote Config の導入
  - A/B Testing の実装・分析
  - Perfomance・Crashlytics・Messaging

#### 業務経験がないこと
  - Firestore・Authentication など上記以外のサービス

### サーバーサイド
#### できること
  - Ruby on Rails を使った一般的なWebアプリケーション開発
    - Migration, MVC, Spec の設計・実装
    - Sidekiq, DelayedJob を使ったバックエンドジョブの設計・実装
  - 責務が分離された設計

#### 業務経験がないこと
  - 高度な Ruby コーディング
  - Rails や Ruby の最新動向のキャッチアップ
  - Ruby on Rails 以外のフレームワークでの開発

### マネジメント
#### 経験があること
  - 3 ~ 5 人のエンジニアとデザイナーからなるチームのプロジェクトマネジメント
    - アーキテクトや実装者と兼務したプレイングマネージャー
    - タスク状況の見える化とタスク完了への意識づけ
    - 事業部や経営層との仕様やスケジュールの合意形成
    - ふりかえりを使った定期的なチーム課題の共有と改善活動
  - 3 ~ 5 人チーム * 2を統括した全体マネジメント
  - [リモートワーク時のパフォーマンス低下への改善案の立案と実行](https://hira22.github.io/Articles/リモートワークでのプロジェクトマネジメント.html)

#### 業務経験がないこと
  - 人事評価
    - 個人へのフィードバックや 1on1 を通じたチーム改善は行っているが、人事評価は行っていない
  - 採用
    - 採用面談の経験はあるが、採用プロセスの設計や立案は行っていない

## プロダクト開発への考え
### 事業のためのプロダクト開発と考える
- その機能は事業に何をもたらし、なぜ今それが必要なのかを考える
- MVPを考え、最初から全てを開発しようとしない


### どうすれば早くデリバリーできるのかを考える
- フィードバックがなければ、正しい改善はできないと考える

### 一時の最高ではなく、変化に柔軟なプロダクトを目指す
- 言語機能・設計・APIの変化を取りこめる状態を保つ
-  シンプルであることを重視する 

### 属人性を排除することを考える
- 理解しやすいコードとドキュメントをつくる
- 決断・行動に至ったプロセスを共有する