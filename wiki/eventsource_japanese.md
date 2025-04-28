<!--
Meta Description: # EventSource: JavaScript におけるサーバー送信イベントの利用 ## 概要 `EventSource` は、サーバーからクライアントへリアルタイムでデータを送信するための JavaScript API です。この API は、特にライブデータや通知を扱うアプリケーションで有効...
Meta Keywords: eventsource, javascript, event, res, const
-->

# EventSource: JavaScript におけるサーバー送信イベントの利用

## 概要
`EventSource` は、サーバーからクライアントへリアルタイムでデータを送信するための JavaScript API です。この API は、特にライブデータや通知を扱うアプリケーションで有効です。

## ドキュメンテーション
`EventSource` は、サーバーサイドで生成されたイベントをクライアントに受信するためのインターフェースです。HTTP プロトコルを使用してデータをストリーミングし、サーバーからのメッセージをリアルタイムで受け取ることができます。

### 目的
`EventSource` を使用することで、クライアントはサーバーからのイベントを非同期に受信し、ページをリロードすることなくデータを更新することができます。

### 使用方法
`EventSource` のインスタンスを作成するには、次のようにします。

```javascript
const eventSource = new EventSource('サーバーのURL');
```

インスタンス化後、イベントリスナーを追加して、サーバーからのメッセージを受信します。

```javascript
eventSource.onmessage = function(event) {
    console.log(event.data);
};
```

### 詳細
- **イベントの種類**: `EventSource` は `message`, `open`, `error` の3つのイベントをサポートしています。
- **CORS**: 異なるオリジンからのリクエストには CORS 設定が必要です。
- **再接続**: 接続が切れた場合、`EventSource` は自動的に再接続を試みます。

## 例
以下は、`EventSource` を用いた基本的な使い方の例です。

### サーバー側 (Node.js を使用)
```javascript
const express = require('express');
const app = express();

app.get('/events', (req, res) => {
    res.setHeader('Content-Type', 'text/event-stream');
    res.setHeader('Cache-Control', 'no-cache');
    res.setHeader('Connection', 'keep-alive');

    setInterval(() => {
        res.write(`data: ${new Date().toLocaleTimeString()}\n\n`);
    }, 1000);
});

app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
});
```

### クライアント側
```javascript
const eventSource = new EventSource('http://localhost:3000/events');

eventSource.onmessage = function(event) {
    console.log('Received:', event.data);
};
```

## 説明
`EventSource` を使用する際の一般的な注意点や落とし穴について説明します。

- **ブラウザの互換性**: `EventSource` は、最新のブラウザでは広くサポートされていますが、一部の古いブラウザでは互換性がない場合があります。
- **エラーハンドリング**: `error` イベントを実装し、接続エラーに対処することが重要です。
- **メッセージの形式**: サーバーから送信されるデータは、必ず `data: <message>\n\n` というフォーマットである必要があります。

## 一文要約
`EventSource` は、サーバーからクライアントへのリアルタイムデータストリーミングを可能にする JavaScript API です。