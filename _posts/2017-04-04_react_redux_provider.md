---
layout: post
title:  "react-reduxのProviderについてまとめ"
date:   2017-03-17
categories: react redux provider
---

## Providerとは

`connect()` 以下のコンポーネント階層の呼び出しでReduxの `store` を使用できるようにします。  
通常は決め文句のようにルートのコンポーネントをラップして使用しますが、`connect` や `store` を理解する上で、併せてまとめようと思います。

## まず最初に

公式サイトにあるサンプルですがRouterを使った場合と使わなかった場合で下記のように、ルートのコンポーネントをラップして使用します。

#### Routerを使わない場合

```js
ReactDOM.render(
  <Provider store={store}>
    <MyRootComponent />
  </Provider>,
  rootEl
)
```

#### Routerを使った場合

```js
ReactDOM.render(
  <Provider store={store}>
    <Router history={history}>
      <Route path="/" component={App}>
        <Route path="foo" component={Foo}/>
        <Route path="bar" component={Bar}/>
      </Route>
    </Router>
  </Provider>,
  document.getElementById('root')
)
```

## connectについて

ReactのコンポーネントをReduxの `store` に接続します。  
一般的に `connect` の一連の流れをラップしたAPIとして `connectAdvanced` を使用します。

**構文**

```js
connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])
```

**引数**

- mapStateToProps
  - この引数を指定するとストアの更新をサブスクライブします
  - ストアが更新されるたびに `mapStateToProps` が呼び出されます
- mapDispatchToProps
- mergeProps
- options

#### 使用例

```js
// ストア更新のときに呼び出される
const ExampleContainer = ({ actions }) => (
  <div>
    <h2>Connect Example</h2>

    <p>connectのサンプルです</p>
  </div>
);

//
const mapStateToProps = state => ({
  value: state.runs.value,
});

//
const mapDispatchToProps = dispatch => ({
  actions: {
    run: bindActionCreators(runActions, dispatch),
  },
});

export default connect(mapStateToProps, mapDispatchToProps)(ExampleContainer);
```
