<!--
Meta Description: # GPUShaderStage：JavaScript 中的 GPU 着色器階段 ## 概述 GPUShaderStage 是一個與 JavaScript 相關的概念，主要用於描述圖形處理單元（GPU）中的著色器階段。它在 WebGPU API 中扮演重要角色，允許開發者直接利用 GPU 加速計算和...
Meta Keywords: gpu, const, gpushaderstage, javascript, device
-->

# GPUShaderStage：JavaScript 中的 GPU 着色器階段

## 概述
GPUShaderStage 是一個與 JavaScript 相關的概念，主要用於描述圖形處理單元（GPU）中的著色器階段。它在 WebGPU API 中扮演重要角色，允許開發者直接利用 GPU 加速計算和渲染。

## 文檔
### 目的
GPUShaderStage 定義了 GPU 中不同的著色器階段，如頂點著色器和片段著色器，這些階段用於處理圖形數據和生成最終圖像。它使開發者能夠精確控制圖形渲染過程，從而提高性能和效率。

### 使用方法
在使用 WebGPU 時，開發者需要創建著色器程序並指定其所屬的著色器階段。以下是基本的使用步驟：

1. **創建 GPUDevice**：使用 `navigator.gpu.requestAdapter()` 獲取 GPU 适配器，並創建一個 GPU 設備。
2. **編寫著色器**：使用 WGSL 或 GLSL 編寫著色器代碼。
3. **創建著色器模塊**：將著色器代碼加載到 GPU 內存中。
4. **設置渲染管線**：在渲染管線中指定 GPUShaderStage。

### 詳細信息
- **頂點著色器 (Vertex Shader)**：負責處理每個頂點的數據，例如位置、顏色等。
- **片段著色器 (Fragment Shader)**：負責生成每個像素的最終顏色，通常用於紋理映射和光照計算。
- **其他著色器階段**：如幾何著色器和計算著色器，根據需求可選擇使用。

## 示例
以下是創建簡單 GPU 著色器的示例：

```javascript
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

const vertexShaderCode = `
  @stage(vertex)
  fn main(@location(0) position: vec4<f32>) -> @builtin(position) vec4<f32> {
      return position;
  }
`;

const fragmentShaderCode = `
  @stage(fragment)
  fn main() -> @location(0) vec4<f32> {
      return vec4<f32>(1.0, 0.0, 0.0, 1.0); // 紅色
  }
`;

const vertexShaderModule = device.createShaderModule({ code: vertexShaderCode });
const fragmentShaderModule = device.createShaderModule({ code: fragmentShaderCode });

// 設置渲染管線
const pipeline = device.createRenderPipeline({
    vertex: {
        module: vertexShaderModule,
        entryPoint: 'main',
    },
    fragment: {
        module: fragmentShaderModule,
        entryPoint: 'main',
        targets: [{ format: 'bgra8unorm' }],
    },
});
```

## 解釋
- **常見陷阱**：確保著色器的輸入和輸出正確匹配，否則會導致渲染錯誤。
- **性能考量**：不同的著色器階段性能各異，選擇合適的著色器可大幅提高渲染效率。
- **調試困難**：在 GPU 上運行的著色器可能不易調試，建議使用 WebGPU 的調試工具。

## 一句總結
GPUShaderStage 是 JavaScript 中用於控制 GPU 着色器階段的重要功能，能夠顯著提升圖形渲染性能。