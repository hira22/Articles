#  Install
## npm

細かいことは気にせず、node.js からステーブル版を入れた。

## ask-cli
```
sudo npm install -g ask-cli
```

```
ask configure
```

aws アカウントと紐付けたり、profile を作ったり

### なんかミスった

#### これで解決
~/.ask

を削除して、
```
ask configure
```
からやり直し

#### 起きた問題

> aws アカウントの認証ができるのに、vendor id が紐づいてないと言われる

https://developer.amazon.com/settings/console/mycid

こちらでも確認できるのに…

.ask/cli_config

を書き換えてみたりしたが、何も変わらず。

## VSCode

1. 拡張機能を入れる

    名前: Alexa Skills Kit (ASK) Toolkit
    ID: ask-toolkit.alexa-skills-kit-toolkit
    説明: Build and manage Alexa skills using Visual Studio Code
    バージョン: 2.0.0
    パブリッシャー: Amazon Alexa
    VS Marketplace リンク: https://marketplace.visualstudio.com/items?itemName=ask-toolkit.alexa-skills-kit-toolkit

1. ⌘ + shift + p
1. View: Show Alexa Skills ToolKit
1. Sign in
1. create new skill
