<!--
Meta Description: # XRInputSource：JavaScript 中的虛擬實境輸入來源 ## 簡介 XRInputSource 是一個 JavaScript API，用於描述在虛擬實境（VR）和擴增實境（AR）環境中用戶的輸入設備。該 API 使開發者能夠獲取和處理來自控制器、手部追蹤或其他輸入設備的數據。 #...
Meta Keywords: session, xrinputsource, javascript, api, inputsource
-->

# XRInputSource：JavaScript 中的虛擬實境輸入來源

## 簡介
XRInputSource 是一個 JavaScript API，用於描述在虛擬實境（VR）和擴增實境（AR）環境中用戶的輸入設備。該 API 使開發者能夠獲取和處理來自控制器、手部追蹤或其他輸入設備的數據。

## 文檔
### 目的
XRInputSource 使開發者可以接入用戶的輸入設備，從而提高虛擬實境和擴增實境應用的互動性。這些輸入設備可以是 VR 控制器、手部追蹤設備或其他類型的輸入裝置。

### 使用方法
要使用 XRInputSource，開發者需要透過 WebXR API 獲取 XRSession，然後從中提取輸入來源。

### 詳細說明
```javascript
// 獲取 XRSession
navigator.xr.requestSession('immersive-vr').then(session => {
  session.addEventListener('selectstart', onSelectStart);
  
  // 獲取輸入來源
  session.requestReferenceSpace('local').then(referenceSpace => {
    session.requestAnimationFrame(onXRFrame);
  });
});

// 處理每一幀的 XR 輸入
function onXRFrame(time, frame) {
  const inputSources = frame.session.inputSources;

  inputSources.forEach(inputSource => {
    // 檢查輸入來源的類型
    if (inputSource.handedness === 'right') {
      // 處理右手控制器的輸入
    }
  });

  frame.session.requestAnimationFrame(onXRFrame);
}
```

## 範例
### 基本用法
以下範例展示了如何獲取並處理 XRInputSource 的輸入數據：

```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
  session.addEventListener('selectstart', event => {
    console.log('選擇開始', event.inputSource);
  });

  session.addEventListener('selectend', event => {
    console.log('選擇結束', event.inputSource);
  });
});
```

## 解釋
### 常見陷阱
- **不支持的設備**：並非所有瀏覽器或設備都支持 XRInputSource，開發者應檢查兼容性。
- **事件處理**：必須確保正確添加和移除事件監聽器，以避免內存泄漏或性能問題。
- **空的輸入來源**：在使用輸入來源前，開發者應檢查是否有有效的輸入來源，否則可能會導致錯誤。

## 一句總結
XRInputSource 是一個用於在虛擬實境和擴增實境環境中處理用戶輸入的 JavaScript API。