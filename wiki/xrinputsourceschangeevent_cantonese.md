<!--
Meta Description: # XRInputSourcesChangeEvent：JavaScript 中的虛擬現實輸入源變更事件 ## 概要 XRInputSourcesChangeEvent 是一個與 WebXR API 相關的事件，當虛擬現實 (VR) 或擴增實境 (AR) 環境中的輸入源（如控制器）發生變化時觸發。這...
Meta Keywords: xrinputsourceschangeevent, webxr, javascript, session, api
-->

# XRInputSourcesChangeEvent：JavaScript 中的虛擬現實輸入源變更事件

## 概要
XRInputSourcesChangeEvent 是一個與 WebXR API 相關的事件，當虛擬現實 (VR) 或擴增實境 (AR) 環境中的輸入源（如控制器）發生變化時觸發。這對於開發者來說，能夠即時獲取輸入源的變更狀態，從而提供更流暢的用戶體驗。

## 文檔
### 目的
XRInputSourcesChangeEvent 旨在讓開發者能夠監控 VR/AR 應用程式中輸入源的變更情況，例如添加或移除控制器，從而即時更新應用程式的狀態。

### 使用方法
要使用 XRInputSourcesChangeEvent，開發者需要在 WebXR 環境中設置事件監聽器。當輸入源的數量或類型發生變化時，事件將被觸發。

### 詳細信息
- **事件類型**：XRInputSourcesChangeEvent
- **屬性**：
  - `inputSources`：一個包含當前所有輸入源的數組，這些輸入源是 XRInputSource 的實例。
- **觸發時機**：當有新的輸入源被添加或現有的輸入源被移除時。

## 範例
以下是如何在 JavaScript 中使用 XRInputSourcesChangeEvent 的基本範例：

```javascript
// 確保 WebXR 支援
if (navigator.xr) {
    navigator.xr.requestSession('immersive-vr').then((session) => {
        session.addEventListener('inputsourceschange', (event) => {
            console.log('輸入源已變更:', event.inputSources);
        });

        session.start();
    });
}
```

## 解釋
開發者在使用 XRInputSourcesChangeEvent 時，需注意以下幾點：
- 確保 WebXR API 已正確加載，否則無法捕獲事件。
- 事件可能在多種情況下觸發，因此需合理處理輸入源的添加和移除。
- 不同設備的輸入源類型可能有所不同，開發者需考慮跨設備的兼容性。

## 一句總結
XRInputSourcesChangeEvent 是一個重要的事件，用於監控虛擬現實和擴增實境環境中的輸入源變更。