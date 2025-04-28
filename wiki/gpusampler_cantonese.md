<!--
Meta Description: # GPUSampler：JavaScript 中的 GPU 取樣器 ## 簡介 GPUSampler 是 JavaScript 中用於 WebGPU API 的一個重要組件，專門用於管理圖像取樣和紋理過濾，提升圖形渲染的性能和效果。 ## 文檔 ### 目的 GPUSampler 主要用於定義如何...
Meta Keywords: gpusampler, gpu, repeat, javascript, device
-->

# GPUSampler：JavaScript 中的 GPU 取樣器

## 簡介
GPUSampler 是 JavaScript 中用於 WebGPU API 的一個重要組件，專門用於管理圖像取樣和紋理過濾，提升圖形渲染的性能和效果。

## 文檔
### 目的
GPUSampler 主要用於定義如何從紋理中取樣顏色和其他數據。它支持多種取樣模式和過濾方式，讓開發者能夠靈活地控制渲染結果。

### 用法
要使用 GPUSampler，首先需要創建一個 GPU 計算上下文，然後利用 `device.createSampler()` 方法來創建一個取樣器。以下是 GPUSampler 的主要屬性：

- **magFilter**：控制放大時的取樣過濾方式，可以選擇 `filtering` 或 `nearest`。
- **minFilter**：控制縮小時的取樣過濾方式。
- **addressModeU** 和 **addressModeV**：控制紋理在 U 和 V 軸的地址模式，選擇 `clamp-to-edge`、`repeat` 或 `mirror-repeat`。
- **mipmapFilter**：用於多重紋理時的過濾方式。

#### 範例
以下是一個基本的 GPUSampler 使用範例：

```javascript
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

const sampler = device.createSampler({
    magFilter: 'linear',
    minFilter: 'linear',
    addressModeU: 'repeat',
    addressModeV: 'repeat',
    mipmapFilter: 'linear',
});
```

### 解釋
使用 GPUSampler 時，開發者需要注意以下幾點：

- **過濾性能**：選擇合適的過濾方式對性能和質量有直接影響，尤其是在高分辨率場景中。
- **地址模式的選擇**：根據紋理的特性選擇適合的地址模式，避免不必要的性能損失。
- **支持的屬性**：不同的 GPU 可能對 GPUSampler 的支持程度不同，開發者應該測試其在目標設備上的表現。

## 總結
GPUSampler 是一個強大的工具，能夠幫助開發者精確控制圖像取樣，提升 WebGPU 應用的性能和畫質。