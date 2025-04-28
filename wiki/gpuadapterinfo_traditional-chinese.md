<!--
Meta Description: # GPUAdapterInfo: JavaScript 中的 GPU 適配器資訊 ## 摘要 `GPUAdapterInfo` 是 WebGPU API 的一部分，用於提供關於可用 GPU 適配器的詳細資訊，這對於高效能圖形渲染和計算非常重要。 ## 文檔 `GPUAdapterInfo` 物件提...
Meta Keywords: gpu, gpuadapterinfo, console, info, adapter
-->

# GPUAdapterInfo: JavaScript 中的 GPU 適配器資訊

## 摘要
`GPUAdapterInfo` 是 WebGPU API 的一部分，用於提供關於可用 GPU 適配器的詳細資訊，這對於高效能圖形渲染和計算非常重要。

## 文檔
`GPUAdapterInfo` 物件提供了有關 GPU 適配器的屬性，這些屬性幫助開發者理解可用的硬體資源。它包含以下關鍵屬性：

- **描述 (description)**: 一個字串，提供 GPU 適配器的描述，通常包含製造商和型號。
- **名稱 (name)**: 一個字串，表示 GPU 的名稱。
- **標識 (vendorId)**: 一個整數，代表 GPU 製造商的唯一標識符。
- **設備 ID (deviceId)**: 一個整數，指示特定 GPU 設備的唯一標識符。

這些資訊對於優化性能和選擇合適的 GPU 適配器至關重要。

### 使用方式
要獲取 `GPUAdapterInfo`，首先必須使用 `navigator.gpu.requestAdapter()` 方法來請求 GPU 適配器。當成功獲得適配器後，可以訪問其 `adapterInfo` 屬性以獲取相關資訊。

```javascript
async function getGPUInfo() {
    const adapter = await navigator.gpu.requestAdapter();
    if (adapter) {
        console.log(adapter.info);
    } else {
        console.error("未能獲取 GPU 適配器");
    }
}
```

## 範例
以下是使用 `GPUAdapterInfo` 的基本範例：

```javascript
async function displayGPUInfo() {
    const adapter = await navigator.gpu.requestAdapter();
    if (adapter) {
        const info = adapter.info;
        console.log("GPU 名稱: " + info.name);
        console.log("GPU 描述: " + info.description);
        console.log("廠商 ID: " + info.vendorId);
        console.log("設備 ID: " + info.deviceId);
    } else {
        console.log("無法獲取 GPU 適配器");
    }
}

displayGPUInfo();
```

## 解釋
在使用 `GPUAdapterInfo` 時，開發者應注意以下幾點：

1. **瀏覽器支持**: 目前，並非所有瀏覽器都支持 WebGPU，因此在使用此功能前需檢查支持情況。
2. **非同步請求**: `requestAdapter()` 方法是非同步的，確保使用 `async/await` 或其他異步處理方式來獲取適配器資訊。
3. **錯誤處理**: 若無法獲取適配器，應妥善處理錯誤，提供用戶友好的反饋。

## 總結
`GPUAdapterInfo` 物件提供了關於 GPU 適配器的重要資訊，幫助開發者在 JavaScript 中進行高效能圖形和計算應用的開發。