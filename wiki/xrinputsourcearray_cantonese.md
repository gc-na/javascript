<!--
Meta Description: # XRInputSourceArray：JavaScript 中的虛擬現實輸入源陣列 ## 簡介 `XRInputSourceArray` 是一個在 WebXR API 中使用的類型，允許開發者管理和操作來自虛擬現實（VR）或擴增實境（AR）設備的輸入源。這個類型提供了一個方便的方式來訪問和控制所...
Meta Keywords: xrinputsourcearray, inputsources, javascript, xrinputsource, session
-->

# XRInputSourceArray：JavaScript 中的虛擬現實輸入源陣列

## 簡介
`XRInputSourceArray` 是一個在 WebXR API 中使用的類型，允許開發者管理和操作來自虛擬現實（VR）或擴增實境（AR）設備的輸入源。這個類型提供了一個方便的方式來訪問和控制所有可用的輸入裝置，如控制器和手柄。

## 文檔
### 目的
`XRInputSourceArray` 的主要目的是提供一個接口來存取和操作在 XR 環境中的輸入設備。藉由這個接口，開發者可以輕鬆地獲取輸入事件並進行相應處理。

### 用法
`XRInputSourceArray` 是一個陣列，包含了所有當前連接的輸入源。開發者可以透過 `XRSession` 的 `inputSources` 屬性來獲取這個陣列，然後可以對陣列中的每個 `XRInputSource` 進行操作。

#### 基本語法
```javascript
let inputSources = xrSession.inputSources;
```

### 詳細信息
- **屬性**:
  - `length`: 返回當前輸入來源的數量。
  - `XRInputSource`: 陣列中的每個元素都是一個 `XRInputSource` 物件，包含該輸入源的詳細信息，如類型、位置和狀態。

## 例子
以下是一個簡單的範例，顯示如何使用 `XRInputSourceArray` 來獲取和顯示連接的輸入源信息：

```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
  session.addEventListener('selectstart', function(event) {
    let inputSources = session.inputSources;
    inputSources.forEach((source) => {
      console.log(`輸入源類型: ${source.targetRayMode}`);
    });
  });
});
```

在這個例子中，當使用者開始選擇時，會列出所有可用的輸入源及其類型。

## 解釋
在使用 `XRInputSourceArray` 時，開發者需要注意以下幾點：
- 確保在進行任何操作前，XR 環境已經正確初始化。
- 當用戶移除或添加輸入設備時，`inputSources` 陣列會動態變化，因此應當在每次事件中重新獲取輸入源。
- 不同的設備可能會有不同的輸入行為，因此開發者應仔細測試各種設備的兼容性。

## 總結
`XRInputSourceArray` 讓開發者能夠有效管理虛擬現實和擴增實境中的輸入設備，從而提升用戶互動體驗。