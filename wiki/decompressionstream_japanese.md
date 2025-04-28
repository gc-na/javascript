<!--
Meta Description: # DecompressionStream: JavaScriptにおけるストリームデータの解凍 ## 概要 `DecompressionStream`は、JavaScriptにおいて圧縮データを解凍するためのストリームAPIです。この機能は、Webアプリケーションでのデータ転送の効率を向上させるた...
Meta Keywords: decompressionstream, const, new, readablestream, controller
-->

# DecompressionStream: JavaScriptにおけるストリームデータの解凍

## 概要
`DecompressionStream`は、JavaScriptにおいて圧縮データを解凍するためのストリームAPIです。この機能は、Webアプリケーションでのデータ転送の効率を向上させるために使用されます。

## ドキュメンテーション
`DecompressionStream`は、バイナリデータを解凍するためのインターフェースを提供します。主に、HTTPレスポンスやファイルストレージから取得した圧縮データをストリームとして処理する際に利用されます。このAPIは、`ReadableStream`と`WritableStream`の組み合わせにより、データのストリーミング処理が可能です。

### 使用方法
`DecompressionStream`を使用するには、まず圧縮されたデータを含むストリームを作成し、そのストリームを`DecompressionStream`に渡します。以下は基本的な使用手順です。

1. `DecompressionStream`インスタンスを作成します。
2. 圧縮されたデータを読み込むための`ReadableStream`を作成します。
3. `DecompressionStream`を使用して、圧縮データを解凍します。

### 詳細
- **サポートされている圧縮形式**: `gzip`や`deflate`などの一般的な圧縮形式がサポートされています。
- **非同期処理**: ストリーム操作は非同期に行われるため、Promiseやasync/awaitを使用して処理を行うことができます。

## 例
以下は`DecompressionStream`の基本的な使用例です。

```javascript
// 圧縮データを持つReadableStreamを作成
const compressedStream = new ReadableStream({
  start(controller) {
    // 圧縮データをプッシュ
    controller.enqueue(new Uint8Array([/* 圧縮データ */]));
    controller.close();
  }
});

// DecompressionStreamのインスタンスを作成
const decompressionStream = new DecompressionStream('gzip');

// 圧縮ストリームを解凍
const decompressedStream = compressedStream.pipeThrough(decompressionStream);

// 解凍されたデータを読み取る
const reader = decompressedStream.getReader();
reader.read().then(({ done, value }) => {
  if (!done) {
    console.log(new TextDecoder().decode(value)); // 解凍されたデータを表示
  }
});
```

## 説明
`DecompressionStream`を使用する際の一般的な落とし穴は、サポートされていない圧縮形式を使用することです。正しい圧縮形式を指定しないと、解凍処理が失敗する可能性があります。また、ストリームの操作は非同期で行われるため、結果を待つためには適切にPromiseやasync/awaitを使用する必要があります。

## 一文の要約
`DecompressionStream`は、JavaScriptにおいてストリームデータを効率的に解凍するためのAPIです。