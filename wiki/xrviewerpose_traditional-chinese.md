<!--
Meta Description: # XRViewerPose：JavaScript中的擴增實境觀察者姿勢 ## 摘要 XRViewerPose 是一個用於 WebXR API 的物件，提供有關擴增實境（AR）或虛擬實境（VR）應用中觀察者的姿勢資訊。它能夠幫助開發者獲取觀看場景的相機位置和方向，從而創建沉浸式的使用者體驗。 ## ...
Meta Keywords: xrviewerpose, viewerpose, webxr, session, api
-->

# XRViewerPose：JavaScript中的擴增實境觀察者姿勢

## 摘要
XRViewerPose 是一個用於 WebXR API 的物件，提供有關擴增實境（AR）或虛擬實境（VR）應用中觀察者的姿勢資訊。它能夠幫助開發者獲取觀看場景的相機位置和方向，從而創建沉浸式的使用者體驗。

## 文檔
### 目的
XRViewerPose 主要用於提供使用者在 VR 或 AR 環境中的位置和朝向資訊。這些資訊對於在三維空間中正確渲染物件至關重要。

### 使用方法
XRViewerPose 是由 `XRFrame` 物件中的 `getViewerPose()` 方法所返回的。開發者可以通過以下方式來取得觀察者的姿勢：

```javascript
let viewerPose = xrFrame.getViewerPose(xrReferenceSpace);
```

### 詳細信息
- **屬性**：
  - `transform`：這是一個 `XRRigidTransform` 物件，包含觀察者的位置信息（`position`）和方向（`orientation`）。
  - `inputSources`：這是一個包含輸入來源的陣列，例如控制器或手勢輸入。

- **注意事項**：
  - 確保在進行姿勢獲取時，XRSession 已經啟動。
  - 需要使用兼容的瀏覽器和設備來支援 WebXR API。

## 範例
以下是一個簡單的範例，顯示如何使用 `XRViewerPose` 來獲取觀察者的姿勢：

```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
    session.requestReferenceSpace('local').then(function(referenceSpace) {
        session.requestAnimationFrame(function render(time, frame) {
            let viewerPose = frame.getViewerPose(referenceSpace);
            if (viewerPose) {
                // 使用 viewerPose.transform 來渲染場景
                console.log(viewerPose.transform);
            }
            session.requestAnimationFrame(render);
        });
    });
});
```

## 解釋
- **常見問題**：
  - **不支援的瀏覽器**：某些瀏覽器可能不完全支援 WebXR，請確認使用的瀏覽器版本。
  - **設備限制**：某些設備可能僅支援 VR，而不支援 AR，這可能會影響 `inputSources` 的可用性。

- **額外說明**：
  - 使用 `XRViewerPose` 時，開發者應謹慎處理每一次動畫幀的更新，以避免性能問題。
  - 在多個使用者場景中，可能需要針對每位使用者的 `XRViewerPose` 進行獨立處理。

## 一句話總結
XRViewerPose 是 WebXR API 中用於獲取擴增實境和虛擬實境中觀察者位置和方向的重要物件。