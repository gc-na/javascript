<!--
Meta Description: # JavaScriptのonmessageイベント: Web Workerとメッセージ通信の理解 ## 概要 `onmessage`は、Web Workerとメインスレッド間のメッセージ通信を処理するためのイベントハンドラーです。このイベントは、Workerがメインスレッドからメッセージを受信した...
Meta Keywords: onmessage, event, worker, web, data
-->

# JavaScriptのonmessageイベント: Web Workerとメッセージ通信の理解

## 概要
`onmessage`は、Web Workerとメインスレッド間のメッセージ通信を処理するためのイベントハンドラーです。このイベントは、Workerがメインスレッドからメッセージを受信した際に発火します。Web Workerを使用することで、ブラウザのメインスレッドをブロックすることなく、バックグラウンドで処理を行うことができます。

## ドキュメンテーション
### 目的
`onmessage`は、Web Workerがメインスレッドから送信されたメッセージを受信するために使用されます。このイベントを使用することで、非同期処理が容易になり、アプリケーションのパフォーマンスが向上します。

### 使用法
`onmessage`は、Workerオブジェクトのプロパティとして設定されます。以下の構文で使用します：

```javascript
worker.onmessage = function(event) {
    // メッセージの処理
};
```

### 詳細
- `event`: `onmessage`イベントが発生したときに渡されるイベントオブジェクト。`event.data`を使用して送信されたデータにアクセスできます。
- Workerからメインスレッドへのメッセージ送信は、`postMessage()`メソッドを使用して行います。
- `onmessage`は、メインスレッドおよびWorkerの両方で使用されます。

## 例
### 基本的な使用例
以下は、Web Workerを使用してメインスレッドからメッセージを受信する基本的な例です。

```javascript
// worker.js
self.onmessage = function(event) {
    console.log("受信したメッセージ:", event.data);
    self.postMessage("メッセージを受け取りました: " + event.data);
};

// メインスレッド
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    console.log("Workerからの応答:", event.data);
};

worker.postMessage("こんにちは、Worker!");
```

## 説明
- **一般的な落とし穴**: `onmessage`の設定は、Workerが生成された後に行う必要があります。Workerがメッセージを受信する前に`onmessage`を設定しないと、メッセージを受け取れないことがあります。
- **データ型**: `event.data`は任意のデータ型（文字列、オブジェクトなど）を受け取ることができますが、循環参照を含むオブジェクトは送信できません。
- **エラーハンドリング**: Worker内でのエラーは、`onerror`イベントを使用して処理できます。このイベントは、Worker内のエラーを捕捉するために使用されます。

## 一文要約
`onmessage`は、Web Workerとメインスレッド間でメッセージを受信するための重要なイベントハンドラーです。