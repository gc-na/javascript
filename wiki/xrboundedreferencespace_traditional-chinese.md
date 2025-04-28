<!--
Meta Description: # XRBoundedReferenceSpace：JavaScript中的擴增實境邊界參考空間 ## 摘要 XRBoundedReferenceSpace 是 WebXR API 的一部分，旨在為擴增實境 (AR) 提供一個受限的參考空間，讓開發者能夠更精確地在現實世界中定位虛擬物體。 ## 文檔...
Meta Keywords: xrboundedreferencespace, session, webxr, requestreferencespace, bounded
-->

# XRBoundedReferenceSpace：JavaScript中的擴增實境邊界參考空間

## 摘要
XRBoundedReferenceSpace 是 WebXR API 的一部分，旨在為擴增實境 (AR) 提供一個受限的參考空間，讓開發者能夠更精確地在現實世界中定位虛擬物體。

## 文檔
### 目的
XRBoundedReferenceSpace 允許開發者在一個定義的範圍內進行虛擬物體的放置和互動，這個範圍通常是由用戶在物理環境中標記的。這對於需要精確位置追蹤的 AR 應用程式非常重要。

### 使用
要使用 XRBoundedReferenceSpace，開發者需要先建立一個 WebXR 會話，然後請求一個帶有邊界的參考空間。這需要用到 `XRSession.requestReferenceSpace()` 方法，並傳遞參數 `XRReferenceSpaceType.BOUNDED`。

### 詳細說明
1. **初始化會話**：
   使用 `navigator.xr.requestSession()` 方法來初始化 WebXR 會話。
  
2. **請求參考空間**：
   使用 `session.requestReferenceSpace('bounded')` 來請求邊界參考空間。

3. **邊界定義**：
   用戶必須在真實世界中移動並標記邊界，這通常涉及到 AR 設備的環境檢測功能。

4. **使用參考空間**：
   一旦獲得 XRBoundedReferenceSpace，開發者可以使用該參考空間來定位和渲染虛擬物體。

## 範例
以下是如何使用 XRBoundedReferenceSpace 的基本範例：

```javascript
async function startXR() {
    const session = await navigator.xr.requestSession('immersive-ar');
    const referenceSpace = await session.requestReferenceSpace('bounded');

    session.addEventListener('select', onSelect);

    function onSelect(event) {
        const hitTestSource = session.requestHitTestSource({
            space: referenceSpace
        });

        // 在這裡處理虛擬物體的放置
    }
}
```

## 解釋
### 常見陷阱
- **環境條件**：確保在良好的環境條件下進行邊界的定義，否則可能會導致不準確的追蹤。
- **設備兼容性**：並非所有裝置都支持 XRBoundedReferenceSpace，因此需要檢查裝置的兼容性。
- **使用者互動**：在請求邊界參考空間之前，應該引導使用者進行必要的互動，以確保邊界的準確性。

### 附加注意事項
- XRBoundedReferenceSpace 是建立在用戶的環境檢測基礎上的，因此用戶移動的範圍會影響虛擬物體的表現。
- 開發者應考慮用戶的使用體驗，提供清晰的指引以協助他們標記邊界。

## 一句話總結
XRBoundedReferenceSpace 是一種為擴增實境應用提供精確位置追蹤的邊界參考空間。