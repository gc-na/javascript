<!--
Meta Description: # WebTransportBidirectionalStream：JavaScriptにおける双方向ストリームの完全ガイド ## 概要 `WebTransportBidirectionalStream` は、WebTransport APIの一部であり、クライアントとサーバー間で双方向のデータスト...
Meta Keywords: const, await, webtransport, stream, webtransportbidirectionalstream
-->

# WebTransportBidirectionalStream：JavaScriptにおける双方向ストリームの完全ガイド

## 概要
`WebTransportBidirectionalStream` は、WebTransport APIの一部であり、クライアントとサーバー間で双方向のデータストリームを確立するために使用されます。この機能により、低遅延のデータ通信が可能となり、リアルタイムアプリケーションの開発が容易になります。

## ドキュメント
### 目的
`WebTransportBidirectionalStream` は、WebTransport APIを使用して、クライアントとサーバーとの間で同時にデータを送受信するためのストリームを提供します。このストリームは、特にゲームやチャットアプリケーションなど、双方向通信が重要なシナリオで役立ちます。

### 使用法
`WebTransportBidirectionalStream` を使用するためには、まず `WebTransport` インスタンスを作成し、ストリームを開く必要があります。以下は基本的な流れです。

1. **WebTransportのインスタンスを作成**:
   ```javascript
   const transport = new WebTransport('wss://example.com');
   ```

2. **接続を開く**:
   ```javascript
   await transport.ready;
   ```

3. **双方向ストリームを作成**:
   ```javascript
   const stream = await transport.createBidirectionalStream();
   ```

4. **データの送受信**:
   ```javascript
   const writer = stream.writable.getWriter();
   const reader = stream.readable.getReader();

   // データを送信
   await writer.write(new Uint8Array([1, 2, 3]));

   // データを受信
   const { done, value } = await reader.read();
   ```

### 詳細
- **ストリームの特性**: `WebTransportBidirectionalStream` のストリームは、同時にデータを送受信することができるため、通信の効率が向上します。
- **エラーハンドリング**: ストリームの操作中にエラーが発生する可能性があるため、適切なエラーハンドリングを行うことが重要です。
- **クローズ処理**: 使用が終わったストリームは必ずクローズする必要があります。これにより、リソースの無駄遣いを防ぎます。

## 例
### 基本的な使用例
```javascript
async function initiateTransport() {
   const transport = new WebTransport('wss://example.com');
   await transport.ready;

   const stream = await transport.createBidirectionalStream();
   const writer = stream.writable.getWriter();
   const reader = stream.readable.getReader();

   // データを送信する
   await writer.write(new Uint8Array([1, 2, 3]));

   // データを受信する
   const { done, value } = await reader.read();
   console.log(value);
   
   // ストリームを閉じる
   writer.releaseLock();
   reader.releaseLock();
   stream.close();
}
```

## 説明
### 注意事項
- **ブラウザのサポート**: `WebTransport` APIは、すべてのブラウザでサポートされているわけではありません。使用する前に、必ずブラウザの互換性を確認してください。
- **セキュリティ**: WebTransportはセキュアな接続（WSS）を必要とします。HTTP接続を使用することはできません。
- **データの形式**: ストリームを介して送信されるデータは、`ArrayBuffer` や `TypedArray` などのバイナリデータ形式である必要があります。

## 一文要約
`WebTransportBidirectionalStream` は、WebTransport APIを使用して、クライアントとサーバー間でリアルタイムの双方向データ通信を可能にするストリームです。