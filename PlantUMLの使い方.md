<!-- TOC -->

- [1. クラス図](#1-クラス図)
  - [1.1. 構造](#11-構造)
    - [1.1.1. Class](#111-class)
    - [1.1.2. Class（可視性）](#112-class可視性)
    - [1.1.3. Enum/Interface/Entity](#113-enuminterfaceentity)
  - [1.2. 関連](#12-関連)
    - [1.2.1. 位置関係の指定](#121-位置関係の指定)
    - [1.2.2. 線の種類](#122-線の種類)
      - [1.2.2.1. クラス](#1221-クラス)
      - [1.2.2.2. ER](#1222-er)
  - [1.3. レイアウト](#13-レイアウト)
    - [1.3.1. パーティション](#131-パーティション)
- [2. アクティビティ図](#2-アクティビティ図)
  - [2.1. ノード](#21-ノード)
    - [2.1.1. 開始](#211-開始)
    - [2.1.2. 終端](#212-終端)
    - [2.1.3. 終了](#213-終了)
    - [2.1.4. 制御ノード](#214-制御ノード)
      - [2.1.4.1. 通常の制御](#2141-通常の制御)
      - [2.1.4.2. 受信イベント](#2142-受信イベント)
      - [2.1.4.3. 送信イベント](#2143-送信イベント)
      - [2.1.4.4. 制御ターゲット](#2144-制御ターゲット)
  - [2.2. フロー](#22-フロー)
    - [2.2.1. 条件分岐](#221-条件分岐)
      - [2.2.1.1. if 分岐](#2211-if-分岐)
      - [2.2.1.2. switch 分岐](#2212-switch-分岐)
    - [2.2.2. 非同期処理](#222-非同期処理)
    - [2.2.3. 繰り返し](#223-繰り返し)
      - [2.2.3.1. 後判定](#2231-後判定)
      - [2.2.3.2. 前判定](#2232-前判定)
  - [2.3. レイアウト](#23-レイアウト)
    - [2.3.1. パーティション](#231-パーティション)
    - [2.3.2. レーン](#232-レーン)
- [3. ここから先はまだ使わなそうなので雑においておく…](#3-ここから先はまだ使わなそうなので雑においておく)
  - [3.1. ユースケース図](#31-ユースケース図)
  - [3.2. ステートマシン図](#32-ステートマシン図)
  - [3.3. シーケンス図](#33-シーケンス図)

<!-- /TOC -->

# 1. クラス図

- [もう辛くない！テキストで書く UML クラス図編](https://qiita.com/ykawakami/items/f6688b845945669f0ce5)
- [IT 専科 クラス図](http://www.itsenka.com/contents/development/uml/class.html)
- [PlantUML 　クラス図](https://plantuml.com/ja/class-diagram)

## 1.1. 構造

### 1.1.1. Class

![](./images/UML/Class/HOwnJiCm48PtFyMDoHG1cwVsKTpO0KksWvBBL6LmXLG4P809CL49YKu5n8ZAoxXfuIsu65NnOFa-dV__czGeAcoiORaHTGrJc3C0BJcunivKHSESLb3dhHDMSQYnqkwSSD6u_2H9XmKn8ofoR0TsIcpyD90p8Yrp9Ih0yXBA0gOCwEm_rx_Bwx1u2Fub-Fkmk8ruj-qEsqtmw_xj--TZbKInBDwS5rePUHoimejI9cbA6Vkx.png)

```uml
@startuml
class A {
  id: number
  {static}name: string
  func1()
  {abstract}func2()
  {static}func3()
}
note top of A
    注釈をつける
    位置と対象(class/class::field/class::method())を指定
end note

note left of A::id
    無印/{static}/{abstract}を付加できる
end note
@enduml
```

### 1.1.2. Class（可視性）

![](./images/UML/Class/SoWkIImgAStDuKhEIImkLd1KLwZcKb3GpaonKiWhpKrABGBoTFCISrEj58fBYZBpqe5yvRJIl6H33KqWimx4D08oQxcuyl9BKXMIyajAydCLyjE0Hd4f0C7J_lKlbarxrh3ySTEa5mjNFE_VzxXn-UF6tiTDtM1v9MqbpeBIf9pCP0XN5yWjoYnBB4c5y9ML50gAW2OdbwIcG4JgW2eIaxCJqrEvKlDI543MSZa0MK1V0000.png)

```uml
@startuml
class A' {
  +id: number
  -name: string
  #func1()
  ~func2()
}

note bottom of A'
    可視性を表現できる
    "+"	public
    "-"	private
    "#" protected
    "~"	package
end note
@enduml
```

### 1.1.3. Enum/Interface/Entity

![](./images/UML/Class/SoWkIImgAStDuKhDAyrLS0KHrLmA2YML1Qc6KDe8IAULvYLhQ7BLSd5bvfMa5gKb9gSgUC9OO1sPALOAGDr9gKL0JbvYRggLGd59KMPUEehkrBoIp99A1LSm1TO7qUdf5m9cfsMcvW2vOOv1pXwEGK0T3gbvAK3d0G00.png)

```uml
@startuml
enum Enum {
  type1
  type2
  func()
}

interface Interface {
  id: number
  name: string
  func()
}

entity Entity {
    id: INT
    field: VARCHAR
}
@enduml
```

## 1.2. 関連

### 1.2.1. 位置関係の指定

![](./images/UML/Class/SoWkIImgAStDuNBEIImkLj0jrLK8BO1nYdGLWZBJCqfW_1HT1PVyyZmODqTNmISrhOGhBxyaLI4flwGaFrSXFqq1BCkb00JFjyzwtBZkoTxUvtlNFMwQzAod_UaweCZonuszZvkwkLBpKXH0UhaSW2oW6m00.png)

```uml
@startuml
Class -u- Up
Class -r- Right
Class -d- Down
Class -l- Left
note bottom of Class
    線の位置を指定できる
end note
@enduml
```

### 1.2.2. 線の種類

#### 1.2.2.1. クラス

![](./images/UML/Class/SoWkIImgAStDuShCAqajIajCJbNmXBEgkMgvk9np4ekB3GmLR6fqTHKW72C5gsSR-vxsJDD_lctciyxzN70jG5LwUWXLJzVDVzw_3sg4iO8Mt0GJ1Ql7JPiVDmFHtCTDEnutRN_Sl1p8rN-slFjPnmIe3bC59KCbXNoWBYK3FRqy9QXcCmMhbxFRdczfWIepLu3RQQ5WzRnfv_Fjiw1IbWemAmqDmCu1IN7bvPUaAYGMA_Zv.png)

```uml
@startuml
interface Interface {
}

Class01 <|-- Class02 :汎化/継承
Interface <|.. Class02 :実現
Class03 *-- Class04 :コンポジション/構成
Class05 "1" o-- "0..n" Class06 :集約
Class07 .. Class08 :点線
Class09 -- Class10 :実線

note as NOTE
    よく使う線と線のラベル
end note
@enduml
```

#### 1.2.2.2. ER

![](./images/UML/Class/SoWkIImgAStDuSh8J4bLICqjAAbKo4tDJKejAkRYIiqhoGJo_VDI5QfhOJpVnBnA41SX6O_4DOZFBuh7eYGUbOz35OOo_xmST3MeYg9IY_91Xa7To0MYQsfqTQiXxhGoLB1Io0MoG1BnO9dyQeWZ4V862lb524KGLJNL8CjGrHcYg8Cfh84v5A4Ao8OgWLfPW-9EXAM6N5nv-IMf2ed52dx-8QvS2a3mkAdZSMF_axtx7pUs.png)

```uml
@startuml
hide empty members

entity One {}
entity Many {}
entity One_ {}
entity 0_or_Many {}
entity One__ {}
entity One_or_Many {}
entity One___ {}
entity One_Only {}
entity One____ {}
entity Zero_or_One {}

One ||--{ Many :1 : many
One_ ||--o{ 0_or_Many :1 : 0 or many
One__ ||--|{ One_or_Many :1 : 1 or many
One___ ||--|| One_Only :1 : 1 only
One____ ||--o| Zero_or_One :1 : 0 or 1

note as NOTE
    よく使う線と線のラベル
end note
@enduml
```

## 1.3. レイアウト

### 1.3.1. パーティション

![](./images/UML/Class/PP7FIWCn4CRlUOev5xPF44fhzL3mJm_gFQHZ2QvPsQHug3qq4HNqeY_WeQ88tZm8qkB3Z1KVmrdQxYeTGlAH-UOt4z9qNkL-S9AAKwMFLH-XcwD3wvKtcOMX00vZFUP7IYCS6ZoJijWR3HYE_cNBKiobBEN2Dn8bVsFWZ4NdjhE-qMiD3XosbSCLMwVAEUWKQQLznk2bOGsxgRngQSrWPbQbEraFKobRtKuxDMXzMLUy0Mf9.png)

```uml
@startuml
package Presentation {
    interface View<<View>> {}
    interface Presenter<<Presenter>> {}
}

package BusinessLogic {
    interface UseCase {}
    class Interactor<<UseCase>> {}
}

package DataAccess {
    class Model<<APIClient>> {}
}

View *-- Presenter
Presenter *.. View
Presenter <- UseCase
UseCase <|.. Interactor
Interactor <- Model

note as NOTE
    パーティションを使って機能やレイヤーを区切る
end note
@enduml
```

# 2. アクティビティ図

- [IT 専科 アクティビティ図](http://www.itsenka.com/contents/development/uml/activity.html)
- [PlantUML アクティビティ図](https://plantuml.com/ja/activity-diagram-beta)

## 2.1. ノード

個々のアクションや条件のことです。

### 2.1.1. 開始

![](./images/UML/Activity/Node/SoWkIImgAStDuG8pkBZoyajI5OeoqpDA5AnUJkj-khoRoo4rBmMe0W00.png)

```uml
@startuml
start

note right :開始
@enduml
```

### 2.1.2. 終端

![](./images/UML/Activity/Node/SoWkIImgAStDuIekoI_WuihBBqbLACfCpoXHi7g-jUdvwlLS3gbvAK050000.png)

```uml
@startuml
stop

note right :終端
@enduml
```

### 2.1.3. 終了

![](./images/UML/Activity/Node/SoWkIImgAStDuKhDI-7YoiilILKeoapFAE5I08BdMvkUx6e3Cv_itVzyoeh7ZLCVD_KyRfp_kBdZSVEUnqth7pTlVjmqwMahK6hPymLRdYrkUTmuyt5JDyWy1P1nN0v05j020000.png)

```uml
@startuml
end

note right
    終了
    使用されたトークンを全て破棄する
end note
@enduml
```

### 2.1.4. 制御ノード

#### 2.1.4.1. 通常の制御

![](./images/UML/Activity/Node/SoWkIImgAStDuR9wtBJeSTFwnqtR7pSlVzoysPgBAo-_95MXA3CzeqJ1wcd7jgVx5d8vfEQb05K30000.png)

```uml
@startuml
:アクション;

note right :制御
@enduml
```

#### 2.1.4.2. 受信イベント

![](./images/UML/Activity/Node/SoWkIImgAStDuR9wsZ_zoVw5DbnSUVabgGf5cUaP9GfMZvkMF6wU-RXvy-FcZiUDwvxFtFLyodmWu-c-rcShvtCvfEQb03K30000.png)

```uml
@startuml
:受信<

note right :イベントの発生の待機
@enduml
```

#### 2.1.4.3. 送信イベント

![](./images/UML/Activity/Node/SoWkIImgAStDuR9wsT3uPFz2EowklFoIL8MYpFIC4WMhnqtR7pTjUDpSzRXvzUEcIH0rZnjdFcxgVjgnxUc-XLmEgNafGFq0.png)

```uml
@startuml
:送信>

note right :シグナルを送信する制御
@enduml
```

#### 2.1.4.4. 制御ターゲット

![](./images/UML/Activity/Node/SoWkIImgAStDuR9wtBJgSVEqnqqx7ZSjVzoq_d5pHomNLrv-IQf2KMPwHec2rTEERK_tBNpSkEvnq_x7pNiUDsrwtDmCLFQuSSNZnbMFcxenJU1oICrB0PeE0000.png)

```uml
@startuml
:オブジェクト]

note right :制御のターゲットとなるオブジェクト
@enduml
```

## 2.2. フロー

### 2.2.1. 条件分岐

#### 2.2.1.1. if 分岐

![](./images/UML/Activity/Flow/SoWkIImgAStDuSfCKz1uDdVXaztRD1LACbBp53HAYafJDHMu5830wd7JeiTDwnytRN_SlFnnysPhhjISubG5ZRH48AK9KVAqO-dZndMO2lDICjEukFBoIr8LYZBJCqeKh23MFEreUxff0fS3K07GVW00.png)

```uml
@startuml
if (条件) then (true)
    :アクション;
else (false)
    :別のアクション;
endif

note right :条件分岐
@enduml
```

#### 2.2.1.2. switch 分岐

![](./images/UML/Activity/Flow/SoWkIImgAStDuG8pk3BJ53IUpLtuPFSsHqs5aepKF0MDojHYJGKk1I2mUjoqw77J-iTDsnytBt_SlDcQApMdE1MXnGbP2r4wd8crH44Z9JKjiJId16hkquwbZnlNOIhDIybCu-BAooz9LIZAJCyeKR0gBiyiISvGI4u46WBKydJ1bgSJEhY0tiqlu780gWVw7G00.png)

```uml
@startuml
start
if (条件A) then (yes)
    :アクション;
elseif (条件B) then (yes)
    :アクション;
elseif (条件C) then (yes)
    :アクション;
else (default)
    :別のアクション;
endif

note right :switch case の場合

stop
@enduml
```

### 2.2.2. 非同期処理

![](./images/UML/Activity/Flow/SoWkIImgAStDuKhBByhcKW02gyTDYnuthN_SjFrny_B7pPkjmL8AYUc9cNaG1KyxbZvkN8UXB3KlHG5i2bTUVacgGb5cUaQ9WjMB9UtFfcu0gdyvTzxJ2JtFvin_shxi-OGsBWUWUg350000.png)

```uml
@startuml
fork
    :アクション;
fork again
    :別のアクション;
end fork

note right :複数の非同期処理
@enduml
```

### 2.2.3. 繰り返し

#### 2.2.3.1. 後判定

![](./images/UML/Activity/Flow/SoWkIImgAStDuG8pk8fI2r8JIxWK5AmUDorwtBJ-STFsnytB7pTljePAAPHdPEQaAcWytxdXSLFNY_rJ7ZTEVpPtuPFTspI1HkGNS76bvUGdbcJcfIlavPUaAXHbfcUKA5WXAt_QlkpvXBRtUpgUxkjvsh7awRfPx_TqSZcavgK0tG40.png)

```uml
@startuml
start
repeat
  :アクション;
repeat while (繰り返し条件)
stop

floating note right :繰り返し処理（後判定）
@enduml
```

#### 2.2.3.2. 前判定

![](./images/UML/Activity/Flow/SoWkIImgAStDuG8pkCepCdDI5JIUxzpmkAdhnVufZnkdFvkxyCdkRPfS2WfMZviMFMvQ_xXf--FcvO-RDrjpfUQbW7K0TUSNS76bvUGdbcJcfIlavPUaAXHbfcUKA5WXc_MqVTdp2MtlztGyxUnzsh7awRfPx_TqSZa0ZG4w0G00.png)

```uml
@startuml
start
while (繰り返し条件)
  :アクション;
endwhile
stop

floating note right :繰り返し処理（前判定）
@enduml
```

## 2.3. レイアウト

### 2.3.1. パーティション

![](./images/UML/Activity/Flow/SoWkIImgAStDuIe0qfabcVbv2e-R9pvktlEukUrnq-B7JTiVDoz_tBnPePfB0GYi7ZSjUjoq7YvipLNBnPMNNvAgK9IPdb6YOFLivVmNpNiVDxKydxBxvTn5JtjdFDdR-xXn-TEUNKyxsXytTJzkNF5YMJTGmUF6cOyRMxWSKlDIWFO30000.png)

```uml
@startuml
partition パーティション {
    :アクション;
}

note right :機能や画面単位で区切ると見やすい
@enduml
```

### 2.3.2. レーン

![](./images/UML/Activity/Flow/SoWkIImgAStDuQfvtBpcSVEUnysR3Mkuh1utBNhSjFvnq_R7pSk1GjP8qaPOfF5gC2HLWp4s3LnfEVc99PbvwGfv-IMf2aMPwHab2bPmFO-R9ZtjsVMqe_rnKpUNGsfU2j1F0000.png)

```uml
@startuml
|レーン1|
:アクション;
|レーン2|
:アクション;
:アクション;
|レーン1|
:アクション;
:アクション;
|レーン3|
:アクション;

floating note right :レーンを区切る
@enduml
```

いつ使うかわからない
![](./)

```uml
@startuml
:???/
:???|
:???}
@enduml
```

# 3. ここから先はまだ使わなそうなので雑においておく…

## 3.1. ユースケース図

```uml
@startuml

actor Promoter
actor Entrant

Promoter --> (Create Event)
Promoter -> (Attend Event)

Entrant --> (Find Event)
(Attend Event) <- Entrant

(Attend Event) <.. (Create Member)  : <<include>>

@enduml
```

## 3.2. ステートマシン図

```uml
@startuml

[*] --> active

active -right-> inactive : disable
inactive -left-> active  : enable

inactive --> closed  : close
active --> closed  : close

closed --> [*]

@enduml
```

## 3.3. シーケンス図

```uml
@startuml

actor Entrant

Entrant -> Ticket : Attend Event Request

activate Ticket
Ticket -> Member : Create Member Request

activate Member
Member -> Member : Create Member
Ticket <-- Member : Create Member Response
deactivate Member

Ticket -> Ticket : Create Ticket
Entrant <-- Ticket : Attend Event Response
deactivate Ticket

@enduml
```
