<!--
Meta Description: # globalThis: JavaScriptにおけるグローバルオブジェクトの取得方法 ## 概要 `globalThis`は、JavaScriptのグローバルオブジェクトにアクセスするための統一された手段を提供するキーワードです。これにより、ブラウザ環境やNode.js環境など、異なるJavaS...
Meta Keywords: globalthis, これにより, ブラウザ, node, web
-->

# globalThis: JavaScriptにおけるグローバルオブジェクトの取得方法

## 概要
`globalThis`は、JavaScriptのグローバルオブジェクトにアクセスするための統一された手段を提供するキーワードです。これにより、ブラウザ環境やNode.js環境など、異なるJavaScript実行環境においても一貫した方法でグローバルスコープにアクセスできます。

## ドキュメンテーション
`globalThis`は、JavaScriptのグローバルオブジェクトを参照します。これにより、異なる環境（ブラウザ、Node.js、Web Workerなど）でのグローバルオブジェクトの違いを考慮する必要がなくなります。

### 目的
- 環境に依存せずにグローバルオブジェクトを取得する。
- コードの可搬性を向上させる。

### 使用法
`globalThis`を使用するには、単にそのキーワードを使用するだけです。特別なメソッドや関数を呼び出す必要はありません。

### 詳細
- `globalThis`は、ES2020（ECMAScript 2020）で導入されました。
- これを使用することで、`window`（ブラウザ）、`global`（Node.js）、`self`（Web Worker）など、環境ごとのグローバルオブジェクトを意識することなく利用できます。

## 例
```javascript
// グローバルオブジェクトの取得
console.log(globalThis);

// グローバル変数の設定
globalThis.myGlobalVar = 'Hello, World!';
console.log(myGlobalVar); // "Hello, World!"
```

## 説明
- **互換性**: `globalThis`は、最新のJavaScript環境では広くサポートされていますが、古い環境では利用できない場合があります。そのため、古いJavaScriptエンジンでは他の手段を考慮する必要があります。
- **スコープ**: `globalThis`を使用することで、変数や関数がグローバルスコープに定義されているかどうかを容易に確認できます。
- **安全性**: `globalThis`を使用することで、環境特有のグローバルオブジェクトに依存することなく、より安全にコードを書くことができます。

## 一行要約
`globalThis`は、JavaScriptにおける異なる環境でのグローバルオブジェクトを統一的に扱うためのキーワードです。