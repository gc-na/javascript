<!--
Meta Description: # TextDecoderStream: JavaScriptにおけるテキストデコーダーのストリーム ## 概要 `TextDecoderStream`は、JavaScriptのストリームAPIを使用して、バイナリデータをテキストに変換するためのインターフェースです。この機能は、特にWebアプリケー...
Meta Keywords: textdecoderstream, const, new, decoderstream, readablestream
-->

# TextDecoderStream: JavaScriptにおけるテキストデコーダーのストリーム

## 概要
`TextDecoderStream`は、JavaScriptのストリームAPIを使用して、バイナリデータをテキストに変換するためのインターフェースです。この機能は、特にWebアプリケーションでのデータの処理や通信で役立ちます。

## ドキュメント
### 目的
`TextDecoderStream`は、エンコーディングされたバイナリデータをリアルタイムでデコードし、テキストに変換するために使用されます。これにより、データのストリーミング処理が効率的に行えます。

### 使用法
`TextDecoderStream`は、次のようにインスタンス化できます。

```javascript
const decoderStream = new TextDecoderStream(encoding);
```

- `encoding`: デコードに使用する文字エンコーディングを指定する文字列です。一般的な値には`"utf-8"`や`"utf-16"`などがあります。

### 詳細
`TextDecoderStream`は、ReadableStreamとWritableStreamの組み合わせとして機能します。WritableStreamにバイナリデータを送信すると、ReadableStreamを通じてデコードされたテキストを取得できます。このプロセスは非同期で行われるため、ストリームは段階的にデータを処理できます。

## 例
以下は、`TextDecoderStream`を使った基本的な例です。

```javascript
const { ReadableStream, WritableStream } = require('stream/web');

const decoderStream = new TextDecoderStream('utf-8');
const writableStream = new WritableStream({
  write(chunk) {
    console.log(`Received chunk: ${chunk}`);
  }
});

const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue(new Uint8Array([72, 101, 108, 108, 111])); // "Hello"のUTF-8バイナリ
    controller.close();
  }
});

// ストリームを接続
readableStream.pipeTo(decoderStream.writable);
decoderStream.readable.pipeTo(writableStream);
```

## 説明
- **非同期処理**: `TextDecoderStream`はストリームを使用しているため、データの処理は非同期で行われます。これにより、パフォーマンスが向上します。
- **エンコーディングの指定**: 適切なエンコーディングを指定しないと、デコードに失敗する可能性があります。一般的なエンコーディングを使用することをお勧めします。
- **ストリームの互換性**: `TextDecoderStream`は、他のストリームAPIと組み合わせて使用することができ、柔軟なデータ処理が可能です。

## 一文要約
`TextDecoderStream`は、JavaScriptでバイナリデータをリアルタイムでテキストにデコードするためのストリームAPIです。