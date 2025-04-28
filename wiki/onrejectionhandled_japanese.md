<!--
Meta Description: # JavaScriptの「onrejectionhandled」: Promiseの拒否を扱うイベント ## 概要 `onrejectionhandled` は、JavaScriptのPromiseオブジェクトに関連するイベントであり、Promiseが拒否された際に、その拒否がハンドリングされたと...
Meta Keywords: onrejectionhandled, promise, event, イベントは, catch
-->

# JavaScriptの「onrejectionhandled」: Promiseの拒否を扱うイベント

## 概要
`onrejectionhandled` は、JavaScriptのPromiseオブジェクトに関連するイベントであり、Promiseが拒否された際に、その拒否がハンドリングされたときに発火します。このイベントは、非同期処理のエラーハンドリングを改善し、デバッグを容易にするために使用されます。

## ドキュメンテーション
`onrejectionhandled` イベントは、Promiseの拒否がハンドリングされたときに呼び出されるグローバルイベントです。このイベントは、Promiseが拒否され、後でその拒否が処理された場合に発生します。具体的には、`Promise.prototype.catch()` メソッドや `try...catch` ステートメントを使用して、拒否されたPromiseが適切に処理された際にトリガーされます。

### 使用方法
`onrejectionhandled` イベントは、`window`オブジェクトに対してリスナーを追加することで利用できます。以下は基本的な使用例です。

```javascript
window.addEventListener('rejectionhandled', (event) => {
    console.log('Promiseの拒否がハンドリングされました:', event.promise);
});
```

## 例
以下に、`onrejectionhandled` イベントの基本的な使用例を示します。

```javascript
// onrejectionhandledイベントをリッスンする
window.addEventListener('rejectionhandled', (event) => {
    console.log('拒否が処理されました:', event.promise);
});

// 拒否されたPromiseを作成する
let promise = new Promise((_, reject) => {
    reject('エラーが発生しました');
});

// 拒否をキャッチする
promise.catch((error) => {
    console.log('エラー:', error);
});
```

この例では、Promiseが拒否された後にキャッチされ、その結果として`onrejectionhandled`イベントがトリガーされます。

## 説明
`onrejectionhandled` イベントは、主に次のような役割を果たします：

1. **エラーハンドリングの強化**: Promiseの拒否を適切に処理できていることを確認するために重要です。これにより、未処理の拒否による警告を減少させることができます。

2. **デバッグの容易化**: 開発者は、Promiseが拒否された後にどのように処理されたかを追跡できるため、より良いデバッグが可能になります。

### 注意点
- `onrejectionhandled` は、Promiseが拒否されてからその拒否がハンドリングされるまでの過程でのみ発生します。未処理の拒否によっては発火しません。
- すべてのPromiseが`onrejectionhandled`イベントを発火するわけではなく、あくまでハンドリングされた場合のみです。

## 一行要約
`onrejectionhandled` は、Promiseの拒否が適切に処理されたときに発火するJavaScriptのグローバルイベントです。