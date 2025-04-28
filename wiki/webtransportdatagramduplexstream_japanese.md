<!--
Meta Description: # WebTransportDatagramDuplexStream: JavaScriptにおける新しいデータストリームの利用法 ## 概要 `WebTransportDatagramDuplexStream`は、Web Transport APIの一部であり、ブラウザ間での低遅延なデータ通信を可...
Meta Keywords: const, webtransportdatagramduplexstream, transport, await, webtransport
-->

# WebTransportDatagramDuplexStream: JavaScriptにおける新しいデータストリームの利用法

## 概要
`WebTransportDatagramDuplexStream`は、Web Transport APIの一部であり、ブラウザ間での低遅延なデータ通信を可能にする双方向ストリームです。この機能により、アプリケーションはWebSocketの代替手段として、リアルタイムデータの送受信が簡単に行えるようになります。

## ドキュメント
### 目的
`WebTransportDatagramDuplexStream`は、データグラムの送受信を行うためのストリームで、特にリアルタイムアプリケーション（ゲーム、チャット、ストリーミングなど）に適しています。従来のHTTPプロトコルに比べて、オーバーヘッドが少なく、より効率的にデータを転送できます。

### 使用法
`WebTransportDatagramDuplexStream`は、`WebTransport`接続を確立した後に生成されます。ストリームは、データを送信するための`write()`メソッドと、データを受信するための`readable`プロパティを持っています。

#### 基本的な構文
```javascript
const transport = new WebTransport('wss://example.com');
const datagramStream = await transport.createDatagramStream();
```

### 詳細
このストリームは、データグラムを非同期に送受信するためのメソッドを提供します。以下のメソッドが含まれています。

- **write(data)**: データグラムをストリームに書き込みます。
- **readable**: ストリームからデータを読み取るためのReadableStreamです。

## 例
### 基本的な使用例
以下は、`WebTransportDatagramDuplexStream`を使用してデータを送受信する基本的な例です。

```javascript
async function example() {
    const transport = new WebTransport('wss://example.com');
    
    await transport.ready; // 接続が確立されるのを待つ
    const datagramStream = await transport.createDatagramStream();
    
    // データを送信
    const dataToSend = new Uint8Array([1, 2, 3, 4]);
    await datagramStream.write(dataToSend);
    
    // データを受信
    const reader = datagramStream.readable.getReader();
    const { value } = await reader.read();
    console.log('受信したデータ:', value);
}

example();
```

## 説明
### 一般的な落とし穴
- **接続の確立**: `WebTransport`オブジェクトを生成した後、`ready`プロミスが解決されるまでストリームを作成しないと、接続の問題が発生する可能性があります。
- **データのサイズ制限**: 送信するデータのサイズに制限があるため、大きなデータを送る場合は分割する必要があります。

### その他の注意点
- ストリームは一度だけ使用できるため、再利用する場合は新しいストリームを生成する必要があります。
- エラーハンドリングを適切に行うことで、通信の信頼性を向上させることができます。

## 一文の要約
`WebTransportDatagramDuplexStream`は、JavaScriptを使用してリアルタイムアプリケーションにおける低遅延データ通信を実現するための双方向ストリームです。