<!--
Meta Description: # CloseEvent - JavaScriptでのWebSocketおよびEventSourceの接続終了イベント ## 概要 `CloseEvent` は、WebSocketおよびEventSourceの接続が閉じられた際に発生するイベントを表します。このイベントは、接続の状態や理由をクライア...
Meta Keywords: closeevent, socket, event, console, log
-->

# CloseEvent - JavaScriptでのWebSocketおよびEventSourceの接続終了イベント

## 概要
`CloseEvent` は、WebSocketおよびEventSourceの接続が閉じられた際に発生するイベントを表します。このイベントは、接続の状態や理由をクライアントに通知するために使用されます。

## ドキュメンテーション
### 目的
`CloseEvent` は、WebSocketやEventSourceが閉じられたときに発生し、その状態や理由を示す情報を提供します。

### 使用方法
`CloseEvent` は、イベントリスナーを使用して監視することができます。例えば、WebSocket接続が閉じられたときに特定のアクションを実行するために、次のようにリスナーを設定します。

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('close', (event) => {
    console.log('WebSocketが閉じられました');
    console.log('閉じた理由:', event.reason);
    console.log('コード:', event.code);
});
```

### 詳細
`CloseEvent` オブジェクトは、以下のプロパティを持っています:
- `code`: 接続が閉じられた理由を示す数値。WebSocketの定義されたコードを参照します。
- `reason`: 接続が閉じられた理由を説明するオプションの文字列。
- `wasClean`: 接続が正常に閉じられたかどうかを示すブール値。

## 例
以下は、WebSocketの使用例です。

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('close', (event) => {
    if (event.wasClean) {
        console.log(`接続は正常に閉じられました。コード: ${event.code}, 理由: ${event.reason}`);
    } else {
        console.error('接続が異常に閉じられました');
    }
});

// 接続を閉じる
socket.close(1000, '正常終了');
```

## 説明
`CloseEvent` の使用においての一般的な落とし穴としては、以下の点が挙げられます。
- **接続が異常に閉じられる場合**: `wasClean` プロパティが `false` の場合、エラーハンドリングを考慮する必要があります。
- **コードと理由の使用**: 適切なコードや理由を使用することで、デバッグやログ記録が容易になります。

## 一文の要約
`CloseEvent` は、WebSocketおよびEventSourceの接続が閉じられた際に、その状態や理由を提供する重要なイベントです。