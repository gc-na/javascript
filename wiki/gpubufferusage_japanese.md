<!--
Meta Description: # GPUBufferUsage: JavaScriptにおけるGPUバッファの使用法 ## 概要 `GPUBufferUsage`は、WebGPU APIにおいて、GPUバッファの使用方法を定義するための列挙型です。この機能は、効率的なグラフィックス処理や計算において、GPUリソースの最適化に役立...
Meta Keywords: gpubufferusage, device, copy_dst, vertex, createbuffer
-->

# GPUBufferUsage: JavaScriptにおけるGPUバッファの使用法

## 概要
`GPUBufferUsage`は、WebGPU APIにおいて、GPUバッファの使用方法を定義するための列挙型です。この機能は、効率的なグラフィックス処理や計算において、GPUリソースの最適化に役立ちます。

## ドキュメンテーション
`GPUBufferUsage`は、バッファを作成する際に指定するフラグのセットを提供します。これにより、どのようにバッファが使用されるかを明示的に指定できます。主な用途は、描画や計算シェーダーでのデータ転送、ストレージなどです。

### フラグの種類
- `GPUBufferUsage.COPY_SRC`：バッファのデータを他のバッファまたはテクスチャにコピーするために使用されます。
- `GPUBufferUsage.COPY_DST`：他のバッファやテクスチャからデータをコピーするために使用されます。
- `GPUBufferUsage.VERTEX`：頂点データを格納するためのバッファとして使用されます。
- `GPUBufferUsage.INDEX`：インデックスデータを格納するためのバッファとして使用されます。
- `GPUBufferUsage.UNIFORM`：シェーダーに渡すためのユニフォームデータを格納するためのバッファとして使用されます。
- `GPUBufferUsage.STORAGE`：計算シェーダーにおけるストレージバッファとして使用されます。
- `GPUBufferUsage.TRANSFER_SRC`：データ転送のソースとして使用されます。
- `GPUBufferUsage.TRANSFER_DST`：データ転送のデスティネーションとして使用されます。

### 使用方法
`GPUBufferUsage`は、`GPUDevice.createBuffer()`メソッドを呼び出す際に、`usage`プロパティとして渡されます。

```javascript
const buffer = device.createBuffer({
    size: 1024,
    usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST,
});
```

ここでは、1024バイトのバッファが作成され、頂点データとデータ転送の両方に使用されることを示しています。

## 例
以下は、`GPUBufferUsage`を使った基本的な例です。

```javascript
// WebGPUのデバイスを取得
const device = await navigator.gpu.requestAdapter().requestDevice();

// バッファの作成
const vertexBuffer = device.createBuffer({
    size: 256, // バッファのサイズ
    usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST // 使用法
});

// バッファにデータをコピー
device.queue.writeBuffer(vertexBuffer, 0, new Float32Array([0.0, 1.0, 0.0]));
```

## 説明
`GPUBufferUsage`を使用する際の一般的な落とし穴には、バッファの使用法を適切に指定しないことがあります。例えば、描画用のバッファを作成する際に`COPY_SRC`フラグを指定してしまうと、期待した動作をしない可能性があります。また、バッファのサイズを適切に設定しないと、エラーが発生することがあります。各フラグの意味を理解し、必要なフラグを適切に組み合わせることが重要です。

## 一文の要約
`GPUBufferUsage`は、WebGPU APIにおいてGPUバッファの使用法を定義するための重要な列挙型です。