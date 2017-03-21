---
layout: post
title:  "React+Webpack+Redux で簡単React環境構築！"
date:   2017-03-17
categories: generator react webpack redux
---

## 前提

- `node.js（>=4.5.0 <5.0.0 || >=5.10）` がインストールされていること
- `npm（>=3.0.0）` がインストールされていること

## 初期セットアップ手順

YEOMANというツールを使用してアプリ開発の初期セットアップを行います。  
詳しくは公式サイトを参考にして下さい。  

[https://github.com/stylesuxx/generator-react-webpack-redux](https://github.com/stylesuxx/generator-react-webpack-redux)

#### 初期セットアップ用のジェネレータをインストール

```sh
npm install -g yo
npm install -g generator-react-webpack-redux
```

プロジェクトの作成時間を短縮するために下記も併せてインストールします

```sh
npm install -g phantomjs-prebuilt
```

## コマンド確認

YEOMANのコマンドで初期プロジェクトの作成、および各種部品の雛形を作成することができます。

#### **初期プロジェクトの作成**

```sh
mkdir my-new-project && cd my-new-project
yo react-webpack-redux
```

このコマンドを実行すると対話形式でどのライブラリを使うか聞いてくるので、自分の好みに併せて選択してください。

#### **Reducerの作成**

```sh
yo react-webpack-redux:reducer my/namespaced/reducers/name
yo react-webpack-redux:reducer items
```

実行結果

```sh
create src/reducers/items.js
create test/reducers/itemsTest.js
```

#### **Actionの作成**

```sh
yo react-webpack-redux:action my/namespaced/actions/name
yo react-webpack-redux:action addItem
```

実行結果

```sh
create src/actions/addItem.js
```

#### **Componentの作成**

```sh
yo react-webpack-redux:component my/namespaced/components/name
yo react-webpack-redux:component button
```

実行結果

```sh
create src/components/button.cssmodule.sass
create src/components/Button.js
create test/components/ButtonTest.js
```

#### **Containerの作成**

```sh
yo react-webpack-redux:container my/namespaced/container/Name
yo react-webpack-redux:container wrapper
```

実行結果

```sh
create src/containers/wrapper.js
```

## 動かしてみる

まず何も考えずに起動して確認してみます。

#### 起動コマンド

```sh
npm start
```

このコマンドを実行すると自動で Chrome 上に下記の画面が表示されます。

![初期起動画面]({{site.baseurl}}/images/2017-03-17-startup.png)

`src/components/App.js` を編集してねって表示されるので内容を確認してみます。

```js
import React from 'react';
import YeomanImage from './YeomanImage';
import './app.css';

class AppComponent extends React.Component {

  render() {
    return (
      <div className="index">
        <YeomanImage />
        <div className="notice">
          Please edit <code>src/components/App.js</code> to get started!
        </div>
      </div>
    );
  }
}

AppComponent.defaultProps = {
};

export default AppComponent;
```