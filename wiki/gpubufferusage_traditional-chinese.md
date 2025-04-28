<!--
Meta Description: # GPUBufferUsage：JavaScript 中的 GPU 緩衝區用法 ## 概述 GPUBufferUsage 是一個在 JavaScript 中使用 WebGPU API 的重要屬性，專門用於指定 GPU 緩衝區的用途。它允許開發者在圖形和計算任務中優化性能，確保資源的有效利用。 ##...
Meta Keywords: gpubufferusage, javascript, gpu, device, createbuffer
-->

# GPUBufferUsage：JavaScript 中的 GPU 緩衝區用法

## 概述
GPUBufferUsage 是一個在 JavaScript 中使用 WebGPU API 的重要屬性，專門用於指定 GPU 緩衝區的用途。它允許開發者在圖形和計算任務中優化性能，確保資源的有效利用。

## 文檔
### 目的
GPUBufferUsage 定義了緩衝區的使用方式，可以幫助開發者在創建緩衝區時，根據其最終用途選擇合適的標誌，以提高渲染效率和計算性能。

### 用法
在 WebGPU 中，當你創建 GPU 緩衝區時，可以通過指定 GPUBufferUsage 來設置緩衝區的行為。主要的使用標誌包括但不限於：

- `GPUBufferUsage.VERTEX`: 用於儲存頂點數據。
- `GPUBufferUsage.INDEX`: 用於儲存索引數據。
- `GPUBufferUsage.UNIFORM`: 用於儲存需要於渲染過程中頻繁更新的數據。
- `GPUBufferUsage.STORAGE`: 用於儲存計算著色器使用的數據。

### 詳細信息
在創建 GPU 緩衝區時，可以通過 `device.createBuffer` 方法來使用 GPUBufferUsage。例如：

```javascript
const buffer = device.createBuffer({
    size: bufferSize,
    usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST
});
```

在這個例子中，緩衝區被設置為可以用作頂點數據和複製目的地。

## 範例
以下是一些基本的使用範例：

### 創建頂點緩衝區
```javascript
const vertexBuffer = device.createBuffer({
    size: vertexData.byteLength,
    usage: GPUBufferUsage.VERTEX,
    mappedAtCreation: true
});
new Float32Array(vertexBuffer.getMappedRange()).set(vertexData);
vertexBuffer.unmap();
```

### 創建索引緩衝區
```javascript
const indexBuffer = device.createBuffer({
    size: indexData.byteLength,
    usage: GPUBufferUsage.INDEX,
    mappedAtCreation: true
});
new Uint16Array(indexBuffer.getMappedRange()).set(indexData);
indexBuffer.unmap();
```

## 解釋
在使用 GPUBufferUsage 時，開發者需要注意以下幾點：

- **多重用途**: 可以將多個用途標誌通過位元運算符 `|` 組合使用，但必須確保這些用途是相容的，以免出現性能問題。
- **緩衝區大小**: 在創建緩衝區時，必須根據實際數據大小設置 `size`，否則可能會導致內存溢出或訪問錯誤。
- **映射範圍**: 當使用 `mappedAtCreation` 時，必須在使用後調用 `unmap()`，以釋放資源。

## 一句話總結
GPUBufferUsage 是 JavaScript 中用於指定 GPU 緩衝區用途的屬性，旨在優化圖形渲染和計算性能。