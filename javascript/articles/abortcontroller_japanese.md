<!--
Meta Description: # AbortController: JavaScriptにおけるリクエストの中止管理 ## 概要 `AbortController`は、Fetch APIやその他の非同期操作を管理し、必要に応じて中止するためのインターフェースです。この機能により、未完了のリクエストを制御し、不要なネットワークリソ...
Meta Keywords: abortcontroller, signal, error, controller, const
-->

# AbortController: JavaScriptにおけるリクエストの中止管理

## 概要
`AbortController`は、Fetch APIやその他の非同期操作を管理し、必要に応じて中止するためのインターフェースです。この機能により、未完了のリクエストを制御し、不要なネットワークリソースの使用を回避できます。

## ドキュメント
### 目的
`AbortController`は、非同期操作を実行する際に、その操作を中止するために使用されます。特に、HTTPリクエストや長時間かかる処理を扱う際に役立ちます。

### 使用法
`AbortController`は、2つの主要な部分で構成されています:
1. **AbortControllerインスタンスの作成**: 新しいAbortControllerを作成します。
2. **AbortSignalの取得**: コントローラーからAbortSignalを取得し、これを使用してFetchリクエストなどに関連付けます。

#### 基本的な構文
```javascript
const controller = new AbortController();
const signal = controller.signal;
```

### 詳細
- **abort()メソッド**: コントローラーの`abort`メソッドを呼び出すと、関連付けられたすべてのAbortSignalが中止され、対応するPromiseが拒否されます。
- **AbortSignal**: リクエストが中止されたかどうかを確認するために使用します。`signal.aborted`プロパティをチェックすることで、状態を確認できます。

## 例
以下は、`AbortController`を使用したシンプルな例です。

### 例1: Fetchリクエストの中止
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://example.com/data', { signal })
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Fetch aborted');
    } else {
      console.error('Fetch error:', error);
    }
  });

// 5秒後にリクエストを中止
setTimeout(() => {
  controller.abort();
}, 5000);
```

### 例2: 長時間の処理の中止
```javascript
const controller = new AbortController();
const signal = controller.signal;

const longRunningTask = new Promise((resolve, reject) => {
  signal.addEventListener('abort', () => {
    reject(new Error('Task aborted'));
  });

  // 仮の長時間処理
  setTimeout(() => {
    resolve('Task completed');
  }, 10000);
});

longRunningTask
  .then(result => console.log(result))
  .catch(error => console.error(error));

// 3秒後に処理を中止
setTimeout(() => {
  controller.abort();
}, 3000);
```

## 説明
`AbortController`を使用する際の一般的な落とし穴には、以下が含まれます。
- **中止の確認**: 中止されたかどうかを確認するために、`signal.aborted`を確認することが重要です。これを怠ると、意図しないエラーが発生する可能性があります。
- **複数回の中止**: 同じAbortControllerインスタンスを使用して、リクエストを複数回中止することはできません。中止後に再利用するとエラーが発生します。
- **非同期処理の中断**: 非同期処理の中止は、Promiseの解決や拒否をトリガーするため、適切にエラーハンドリングを行う必要があります。

## 一文要約
`AbortController`は、JavaScriptにおいて非同期リクエストを中止するための強力なツールです。