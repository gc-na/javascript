<!--
Meta Description: # XRInputSource：JavaScript 中的擴增實境輸入來源 ## 簡介 XRInputSource 是 WebXR API 的一部分，允許開發者管理虛擬與擴增實境中的輸入裝置，使得用戶能夠以自然的方式與虛擬環境進行互動。這些輸入來源可以是控制器、觸控板或其他支持的裝置。 ## 文檔 ...
Meta Keywords: xrinputsource, webxr, session, inputsource, handedness
-->

# XRInputSource：JavaScript 中的擴增實境輸入來源

## 簡介
XRInputSource 是 WebXR API 的一部分，允許開發者管理虛擬與擴增實境中的輸入裝置，使得用戶能夠以自然的方式與虛擬環境進行互動。這些輸入來源可以是控制器、觸控板或其他支持的裝置。

## 文檔
### 目的
XRInputSource 提供了一個接口來獲取與用戶互動的輸入設備的詳細資訊。這在開發擴增實境 (AR) 和虛擬實境 (VR) 應用時至關重要，因為它允許開發者根據不同的輸入設備進行相應的操作。

### 使用方法
XRInputSource 通常與 XRSession 結合使用。當 XRSession 開始時，可以通過 `getInputSources()` 方法獲取當前的輸入來源列表。每個 XRInputSource 物件包含多個屬性，例如 `handedness`（表示使用者的左右手）、`gamepad`（與控制器的映射信息）、`targetRayMode`（顯示輸入的方式）等。

### 詳情
- **屬性**：
  - `handedness`: 表示輸入來源的屬性，可能的值為 "left"、"right" 或 "none"。
  - `targetRayMode`: 描述輸入來源的目標射線模式，可能的值包括 "gaze"、"tracked-pointer" 和 "screen"。
  - `gamepad`: 包含有關遊戲手把的詳細信息，例如按鈕的狀態和觸發器的壓力。

- **方法**：
  - 無需直接調用方法，XRInputSource 是由 WebXR API 自動管理的。

## 範例
以下是使用 XRInputSource 的基本範例：

```javascript
// 開始 XR Session
navigator.xr.requestSession('immersive-vr').then(function(session) {
    session.addEventListener('selectstart', onSelectStart);

    function onSelectStart(event) {
        const inputSource = event.inputSource;
        console.log(`使用者選擇了 ${inputSource.handedness} 手.`);
    }
    
    // 獲取當前的輸入來源
    const inputSources = session.getInputSources();
    inputSources.forEach(inputSource => {
        console.log(`輸入來源: ${inputSource.handedness}`);
    });
});
```

## 解釋
在使用 XRInputSource 時，開發者需要注意以下幾點：
- 確保設備支持 WebXR，否則可能無法獲得任何輸入來源。
- 在獲取輸入來源之前，應先啟動 XR Session。
- 不同的瀏覽器對 WebXR 的支持程度不同，因此在不同環境下測試應用程序是必要的。

## 一句總結
XRInputSource 是 WebXR API 中用於管理虛擬和擴增實境輸入裝置的重要組件。