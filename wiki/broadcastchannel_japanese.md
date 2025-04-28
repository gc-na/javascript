<!--
Meta Description: # BroadcastChannel: JavaScriptでのクロスタブ通信 ## 概要 `BroadcastChannel`は、異なるブラウザタブやウィンドウ間でメッセージを簡単に送受信するためのWeb APIです。この機能を使用することで、同一オリジン内の複数のコンテキストでデータを共有できま...
Meta Keywords: broadcastchannel, channel, postmessage, onmessage, event
-->

# BroadcastChannel: JavaScriptでのクロスタブ通信

## 概要
`BroadcastChannel`は、異なるブラウザタブやウィンドウ間でメッセージを簡単に送受信するためのWeb APIです。この機能を使用することで、同一オリジン内の複数のコンテキストでデータを共有できます。

## ドキュメンテーション
`BroadcastChannel` APIは、同じオリジンの異なるブラウザタブやウィンドウ間でメッセージを送信するための手段を提供します。このAPIを使用することで、アプリケーションの状態をリアルタイムで同期することが可能です。

### 使用法
`BroadcastChannel`のインスタンスを作成するには、チャンネル名を指定します。次に、`postMessage`メソッドを使用してメッセージを送信し、`onmessage`イベントリスナーを使ってメッセージを受信します。

```javascript
// チャンネルの作成
const channel = new BroadcastChannel('my_channel');

// メッセージを送信
channel.postMessage('Hello from another tab!');

// メッセージの受信
channel.onmessage = (event) => {
    console.log('Received:', event.data);
};

// チャンネルのクローズ
channel.close();
```

### 詳細
- **チャンネルの作成**: `BroadcastChannel`のコンストラクタにチャンネル名を渡します。チャンネル名は、メッセージを送受信するための識別子となります。
- **メッセージの送信**: `postMessage`メソッドを使用して、チャンネルにメッセージを送ります。メッセージは任意のデータ型（文字列、オブジェクトなど）を送信できます。
- **メッセージの受信**: `onmessage`イベントリスナーで、受信したメッセージを処理します。このイベントは、同じチャンネルでメッセージが送信されたときに発火します。
- **チャンネルのクローズ**: 使用が終わったチャンネルは`close`メソッドで閉じることが推奨されます。

## 例
以下は、`BroadcastChannel`の基本的な使用例です。

```javascript
// チャンネルの作成
const channel = new BroadcastChannel('test_channel');

// メッセージの送信
channel.postMessage('Hello World!');

// メッセージの受信
channel.onmessage = (event) => {
    console.log(`Received: ${event.data}`);
};

// チャンネルを閉じる
channel.close();
```

## 説明
- **同一オリジン制約**: `BroadcastChannel`は、同一オリジン（スキーム、ホスト、ポートが同じ）内でのみ機能します。異なるオリジン間ではメッセージを送受信できません。
- **パフォーマンス**: 多くのメッセージを送信する場合、受信側での処理がボトルネックになる可能性があります。必要に応じて、メッセージの内容や頻度を調整することが重要です。
- **ブラウザのサポート**: `BroadcastChannel`は、現代の主要なブラウザでサポートされていますが、古いブラウザでは利用できない場合があります。使用前に互換性を確認することをお勧めします。

## 一文要約
`BroadcastChannel`は、同一オリジン内の異なるブラウザタブやウィンドウ間でメッセージを簡単に送受信するためのJavaScript APIです。