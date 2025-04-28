<!--
Meta Description: # GPUSampler：JavaScript 中的高效 GPU 取樣器 ## 簡介 GPUSampler 是一個用於在 WebGPU API 中進行高效 GPU 資源取樣的功能。它擴展了 JavaScript 的圖形渲染能力，使開發者能夠更靈活地處理圖像和紋理，從而在網頁應用程序中實現更高效的圖形...
Meta Keywords: gpusampler, device, linear, javascript, const
-->

# GPUSampler：JavaScript 中的高效 GPU 取樣器

## 簡介
GPUSampler 是一個用於在 WebGPU API 中進行高效 GPU 資源取樣的功能。它擴展了 JavaScript 的圖形渲染能力，使開發者能夠更靈活地處理圖像和紋理，從而在網頁應用程序中實現更高效的圖形處理。

## 文檔
### 目的
GPUSampler 的主要目的是提供一個接口，讓開發者能夠對 GPU 資源進行取樣操作，從而支持高效的圖形渲染及計算。

### 使用方法
在 JavaScript 中使用 GPUSampler 需要先創建一個 WebGPU 上下文，然後調用 `device.createSampler()` 方法來生成一個 GPUSampler 實例。以下是創建 GPUSampler 的基本語法：

```javascript
const sampler = device.createSampler({
    magFilter: 'linear',
    minFilter: 'linear',
    mipmapFilter: 'linear',
    addressModeU: 'repeat',
    addressModeV: 'repeat',
    addressModeW: 'repeat',
    maxAnisotropy: 16,
    maxLod: 10,
    minLod: 0,
    lodMinClamp: 0,
    lodMaxClamp: 10,
});
```

### 參數詳解
- `magFilter`: 指定放大時的過濾模式，支持值為 'nearest' 或 'linear'。
- `minFilter`: 指定縮小時的過濾模式，支持值為 'nearest' 或 'linear'。
- `mipmapFilter`: 指定多重採樣的過濾模式。
- `addressModeU`, `addressModeV`, `addressModeW`: 指定 U、V 和 W 軸的地址模式，支持 'repeat', 'clamp-to-edge', 'mirror-repeat'。
- `maxAnisotropy`: 指定最大各向異性，範圍為 1 到 16。
- `maxLod`, `minLod`: 分別指定最大和最小的 LOD。
- `lodMinClamp`, `lodMaxClamp`: 指定 LOD 的最小和最大夾緊值。

## 範例
以下是使用 GPUSampler 的基本範例：

```javascript
const canvas = document.getElementById('canvas');
const context = canvas.getContext('webgpu');

const device = await context.requestDevice();
const sampler = device.createSampler({
    magFilter: 'linear', 
    minFilter: 'linear',
    addressModeU: 'clamp-to-edge',
    addressModeV: 'clamp-to-edge',
});

// 在渲染管線中使用 sampler
const pipeline = device.createRenderPipeline({
    // ... 其他渲染管線設置 ...
    fragment: {
        module: device.createShaderModule({ code: fragmentShaderCode }),
        entryPoint: 'main',
        targets: [{ format: context.getPreferredFormat(device) }],
    },
    primitive: { topology: 'triangle-list' },
});

// 使用 sampler 進行渲染
```

## 說明
在使用 GPUSampler 時，開發者需要注意以下幾點：
- 確保所有參數都正確設置，特別是過濾模式和地址模式，這會影響最終渲染效果。
- 當設置 `maxAnisotropy` 時，應根據 GPU 的能力進行調整，避免設定超出範圍的值。
- GPUSampler 的性能可能會隨著不同的 GPU 硬體而有所不同，測試和調優是必不可少的。

## 一句總結
GPUSampler 是 WebGPU API 中用於高效資源取樣的功能，能夠顯著提高 JavaScript 應用程序中的圖形渲染性能。