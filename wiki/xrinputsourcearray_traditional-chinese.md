<!--
Meta Description: # XRInputSourceArray：JavaScript中的擴增實境輸入源陣列 ## 概述 `XRInputSourceArray` 是 JavaScript 中 WebXR API 的一部分，用於處理增強現實（AR）和虛擬現實（VR）環境中的輸入設備。它提供了一組輸入源，允許開發者獲取有關用...
Meta Keywords: xrinputsourcearray, inputsources, session, inputsource, javascript
-->

# XRInputSourceArray：JavaScript中的擴增實境輸入源陣列

## 概述
`XRInputSourceArray` 是 JavaScript 中 WebXR API 的一部分，用於處理增強現實（AR）和虛擬現實（VR）環境中的輸入設備。它提供了一組輸入源，允許開發者獲取有關用戶的交互信息，如手柄、觸控板等。

## 文檔
`XRInputSourceArray` 是一個陣列，它包含了一組 `XRInputSource` 物件。每個 `XRInputSource` 物件代表一個可用的輸入設備，並提供相關屬性和方法來獲取輸入狀態。通常用於搭配 `XRSession` 使用，以便在 AR/VR 環境中實現更豐富的用戶交互體驗。

### 目的
`XRInputSourceArray` 主要用於：
- 獲取當前可用的輸入設備。
- 監控和處理來自這些輸入設備的用戶交互。

### 使用
要使用 `XRInputSourceArray`，開發者首先需要建立一個 XR 會話，然後透過會話的 `inputSources` 屬性訪問 `XRInputSourceArray`。這可以在每次渲染時檢查輸入狀態，從而實現動態交互。

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', onSelectStart);
});

function onSelectStart(event) {
    const inputSources = event.session.inputSources;
    inputSources.forEach((inputSource) => {
        // 處理每個輸入源
    });
}
```

## 範例
以下是一個基本的示例，展示如何訪問和使用 `XRInputSourceArray`：

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSources = session.inputSources; // 取得輸入源陣列
        inputSources.forEach((inputSource) => {
            console.log(inputSource.handedness); // 輸出手的類型（左或右）
            console.log(inputSource.targetRaySpace); // 輸出目標射線空間
        });
    });
});
```

## 解釋
使用 `XRInputSourceArray` 時，有幾個常見的陷阱需要注意：
- 確保在 XR 會話中使用 `inputSources`，否則會返回空陣列。
- 不同設備可能會提供不同屬性，例如某些手柄可能沒有觸控板或按鈕。
- 在使用 `inputSources` 時，應該在每次幀更新中檢查輸入狀態，以獲得最即時的交互反饋。

## 一句總結
`XRInputSourceArray` 允許開發者在 WebXR 環境中有效地管理和使用多個輸入設備，增強用戶的交互體驗。