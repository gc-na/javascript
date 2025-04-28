<!--
Meta Description: # XRViewport：JavaScript 中擴增實境的視口管理 ## 摘要 XRViewport 是一個在 WebXR API 中使用的介面，專門用於管理擴增實境 (AR) 和虛擬實境 (VR) 環境中的視口。它提供了有關視口的尺寸和位置的詳細資訊，對於創建沉浸式體驗至關重要。 ## 文檔 X...
Meta Keywords: viewport, xrviewport, xrsession, pose, frame
-->

# XRViewport：JavaScript 中擴增實境的視口管理

## 摘要
XRViewport 是一個在 WebXR API 中使用的介面，專門用於管理擴增實境 (AR) 和虛擬實境 (VR) 環境中的視口。它提供了有關視口的尺寸和位置的詳細資訊，對於創建沉浸式體驗至關重要。

## 文檔
XRViewport 介面主要用於獲取關於 XR 會話中視口的資訊。這些資訊包括視口的寬度、高度、以及相對於螢幕的位置信息，這對於渲染 3D 场景至關重要。XRViewport 通常與 XRSession 及 XRFrame 相關聯，能夠輔助開發者更好地控制渲染過程。

### 目的
XRViewport 的主要目的是提供一個易於使用的介面，讓開發者能夠獲取有關視口的詳細屬性，從而在 AR 或 VR 環境中進行準確的圖形渲染。

### 使用方式
使用 XRViewport 時，開發者可以這樣獲得視口的資訊：

```javascript
let xrSession = await navigator.xr.requestSession('immersive-vr');
xrSession.requestAnimationFrame((time, frame) => {
    let pose = frame.getViewerPose(xrReferenceSpace);
    let viewport = pose.views[0].viewport;
    console.log(viewport);
});
```

## 範例
### 基本使用範例
以下是如何使用 XRViewport 的基本示例：

```javascript
navigator.xr.requestSession('immersive-ar').then(session => {
    session.addEventListener('end', () => {
        console.log('Session ended');
    });

    session.requestAnimationFrame((time, frame) => {
        const pose = frame.getViewerPose(referenceSpace);
        if (pose) {
            const viewport = pose.views[0].viewport;
            console.log(`Viewport: ${viewport.x}, ${viewport.y}, ${viewport.width}, ${viewport.height}`);
        }
    });
});
```

## 解釋
在使用 XRViewport 時，有幾個常見的陷阱需要注意：

1. **視口的變化**：視口的尺寸和位置可能會隨著使用者的移動而變化，因此需要在每個動畫幀中檢查它。
2. **XRSession 的狀態**：確保在 XRSession 開始後再獲取視口屬性，否則可能無法獲取正確的資料。
3. **支持的設備**：並非所有的設備都支持 WebXR API，開發者應在開發前確認設備的兼容性。

## 一句話總結
XRViewport 是 WebXR API 中的關鍵介面，提供了在擴增實境和虛擬實境環境中管理視口的詳細資訊。