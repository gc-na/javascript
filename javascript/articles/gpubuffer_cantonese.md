<!--
Meta Description: # GPUBuffer：JavaScript 中的 GPU 緩衝區使用指南 ## 摘要 GPUBuffer 是一個 JavaScript 接口，允許開發者在圖形處理單元（GPU）中高效地儲存和管理數據，尤其在 WebGPU 和其他圖形 API 中非常重要。 ## 文檔 ### 目的 GPUBuffe...
Meta Keywords: gpubuffer, const, gpubufferusage, gpu, javascript
-->

# GPUBuffer：JavaScript 中的 GPU 緩衝區使用指南

## 摘要
GPUBuffer 是一個 JavaScript 接口，允許開發者在圖形處理單元（GPU）中高效地儲存和管理數據，尤其在 WebGPU 和其他圖形 API 中非常重要。

## 文檔
### 目的
GPUBuffer 的主要目的是提供一個高效的方式來在 GPU 上儲存和操作數據。這對於需要大量計算或渲染的應用程序（例如 3D 遊戲或數據可視化）特別有用。

### 使用方法
要創建一個 GPUBuffer，首先需要一個 GPUDevice 實例。然後，你可以使用 `device.createBuffer()` 方法來創建一個緩衝區。以下是創建 GPUBuffer 的基本語法：

```javascript
const gpuBuffer = device.createBuffer({
  size: bufferSize, // 緩衝區大小，以字節為單位
  usage: GPUBufferUsage.VERTEX | GPUBufferUsage.STORAGE, // 使用方式
});
```

### 詳細說明
- **size**: 指定緩衝區的大小，以字節為單位。這個值必須是 256 的倍數。
- **usage**: 定義緩衝區的用途，可以是 `GPUBufferUsage.VERTEX`、`GPUBufferUsage.INDEX`、`GPUBufferUsage.STORAGE` 等的組合。
- **mapping**: 可以使用 `mapAsync()` 方法來將緩衝區映射到 CPU 內存，以便進行讀寫操作。

## 示例
以下是如何創建一個 GPUBuffer 並填充數據的簡單示例：

```javascript
// 創建 GPU 線程
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

// 創建 GPUBuffer
const bufferSize = 1024; // 1KB
const gpuBuffer = device.createBuffer({
  size: bufferSize,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

// 將數據寫入 GPUBuffer
const data = new Float32Array([1.0, 2.0, 3.0, 4.0]);
await gpuBuffer.mapAsync(GPUMapMode.WRITE);
const mappedRange = gpuBuffer.getMappedRange();
new Float32Array(mappedRange).set(data);
gpuBuffer.unmap();
```

## 解釋
GPUBuffer 的使用可能會遇到一些常見陷阱：
- **大小限制**: 確保緩衝區大小是 256 的倍數，否則將會報錯。
- **使用方式**: 確保選擇的使用方式與你的應用場景一致，否則可能會導致性能問題或錯誤。
- **映射操作**: 使用 `mapAsync()` 進行映射時，必須確保緩衝區已經創建並且處於可映射狀態。

## 一句總結
GPUBuffer 是在 JavaScript 中用於高效管理 GPU 數據的關鍵接口。