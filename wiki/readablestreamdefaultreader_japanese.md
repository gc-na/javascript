<!--
Meta Description: # ReadableStreamDefaultReader: JavaScriptにおけるストリームデータの読み取り ## 概要 `ReadableStreamDefaultReader` は、JavaScriptのストリームAPIにおけるデフォルトのリーダーを提供し、ストリームからデータを非同期的...
Meta Keywords: readablestreamdefaultreader, controller, readablestream, const, stream
-->

# ReadableStreamDefaultReader: JavaScriptにおけるストリームデータの読み取り

## 概要
`ReadableStreamDefaultReader` は、JavaScriptのストリームAPIにおけるデフォルトのリーダーを提供し、ストリームからデータを非同期的に読み取るためのインターフェースです。この機能は、大きなデータを効率よく処理するために使用されます。

## ドキュメント
`ReadableStreamDefaultReader` は、`ReadableStream` オブジェクトのインスタンスからデータを読み取るためのリーダーを作成します。ストリームは、データが連続的に供給される場合に便利で、例えばネットワークからのデータ取得やファイルの読み込みに利用されます。

### 使用方法
`ReadableStreamDefaultReader` を使用するためには、まず `ReadableStream` オブジェクトを生成し、そのオブジェクトの `getReader()` メソッドを呼び出します。このメソッドは、ストリームからデータを読み取るためのリーダーを返します。

```javascript
const stream = new ReadableStream({
  start(controller) {
    // ストリームの初期化
  },
  pull(controller) {
    // データをプッシュする処理
  },
  cancel() {
    // ストリームのキャンセル処理
  }
});

const reader = stream.getReader();
```

### 詳細
- **メソッド**:
  - `read()`: ストリームから次のデータを読み取ります。結果は `{ done, value }` というオブジェクトで返され、`done` が `true` の場合はストリームが終了したことを示します。
  - `releaseLock()`: リーダーがストリームからロックを解除します。

- **プロパティ**:
  - `closed`: リーダーが閉じられたかどうかを示すPromiseです。

## 例
以下は、`ReadableStreamDefaultReader` を使用してストリームからデータを非同期的に読み取る基本的な例です。

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue("Hello");
    controller.enqueue("World");
    controller.close();
  }
});

const reader = stream.getReader();

async function readStream() {
  let result;
  while (!(result = await reader.read()).done) {
    console.log(result.value); // "Hello" そして "World"
  }
}

readStream();
```

## 説明
`ReadableStreamDefaultReader` を使用する際の一般的な落とし穴には、ストリームが終了しているにもかかわらず `read()` メソッドを呼び出すことがあります。これにより、`done` プロパティが `true` である結果が返され、データが存在しないことが示されます。また、リーダーを使用した後は、ストリームを適切にロック解除することが重要です。

## 一文の要約
`ReadableStreamDefaultReader` は、JavaScriptのストリームAPIにおいて、ストリームから非同期的にデータを読み取るためのデフォルトのリーダーを提供します。