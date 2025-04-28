<!--
Meta Description: # XRViewerPose：JavaScript 中擴增實境（AR）與虛擬實境（VR）的檢視者姿勢 ## 簡介 XRViewerPose 是一個在 WebXR API 中使用的接口，旨在提供有關用戶在虛擬或擴增實境中的位置和姿勢的信息。這個接口對於開發沉浸式體驗至關重要，因為它幫助開發者獲取有關攝...
Meta Keywords: xrviewerpose, session, javascript, getviewerpose, onxrframe
-->

# XRViewerPose：JavaScript 中擴增實境（AR）與虛擬實境（VR）的檢視者姿勢

## 簡介
XRViewerPose 是一個在 WebXR API 中使用的接口，旨在提供有關用戶在虛擬或擴增實境中的位置和姿勢的信息。這個接口對於開發沉浸式體驗至關重要，因為它幫助開發者獲取有關攝影機和用戶的當前狀態。

## 文檔
### 目的
XRViewerPose 的主要目的是讓開發者能夠獲取用戶在 XR 環境中的姿勢資訊，進而調整其視圖與互動。這個接口可以在 VR 和 AR 應用中用來追蹤用戶的頭部和身體動作。

### 使用方法
XRViewerPose 通常在 XRSession 的 `getViewerPose()` 方法中使用，返回一個 XRViewerPose 對象，該對象包含有關用戶當前位置和姿勢的信息。

### 詳細信息
- **屬性**：
  - `views`：返回一組 XRView 對象，每個對象都代表一個視圖（例如，左眼和右眼）。
  - `transform`：提供一個 XRCoordinateSystem 以表示用戶的當前姿勢。

- **方法**：
  - `getViewerPose()`: 用來獲取當前的 XRViewerPose。

## 示例
以下是如何在 JavaScript 中使用 XRViewerPose 的基本示例：

```javascript
// 創建 XRSession
navigator.xr.requestSession('immersive-vr').then(function(session) {
    session.addEventListener('select', onSelect);
    
    // 啟動 XR 渲染循環
    function onXRFrame(time, frame) {
        const viewerPose = frame.getViewerPose(referenceSpace);
        
        if (viewerPose) {
            viewerPose.views.forEach(view => {
                // 在這裡使用 view 的信息進行渲染
                console.log(view.transform);
            });
        }
        
        session.requestAnimationFrame(onXRFrame);
    }
    
    session.requestAnimationFrame(onXRFrame);
});
```

## 解釋
### 常見陷阱
- 確保在支持 WebXR 的瀏覽器中運行此代碼，否則可能會遇到錯誤。
- 注意在獲取 XRViewerPose 時，必須先檢查它是否為 `null`，因為在某些情況下可能沒有可用的姿勢數據。
- 需要適當設置 XR 的參考空間，才能正確獲取用戶的姿勢信息。

### 附加說明
此 API 仍在不斷發展中，開發者應該定期檢查相關文檔，以獲取最新的功能和最佳實踐。

## 總結
XRViewerPose 是一個關鍵的接口，提供有關用戶在 XR 環境中的姿勢資訊，幫助開發者創建更具沉浸感的體驗。