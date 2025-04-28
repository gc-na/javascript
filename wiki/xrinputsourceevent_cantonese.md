<!--
Meta Description: # XRInputSourceEvent：JavaScript 中的擴增實境輸入源事件 ## 簡介 XRInputSourceEvent 是一個與擴增實境 (AR) 和虛擬實境 (VR) 應用程式相關的重要事件，主要用於處理用戶輸入設備（如控制器、手套等）帶來的事件。在 JavaScript 中，了...
Meta Keywords: xrinputsourceevent, inputsource, javascript, event, session
-->

# XRInputSourceEvent：JavaScript 中的擴增實境輸入源事件

## 簡介
XRInputSourceEvent 是一個與擴增實境 (AR) 和虛擬實境 (VR) 應用程式相關的重要事件，主要用於處理用戶輸入設備（如控制器、手套等）帶來的事件。在 JavaScript 中，了解和使用 XRInputSourceEvent 可以提升用戶體驗，讓開發者更好地管理交互。

## 文檔
XRInputSourceEvent 是一種事件，當 XR 會話中的輸入源（例如 VR 控制器）狀態變更時，會觸發此事件。這個事件的主要目的是讓開發者能夠捕捉輸入源的各種狀態，如按鈕按下、釋放和位置變化。

### 目的
XRInputSourceEvent 使開發者能夠：
- 監聽用戶的輸入動作。
- 獲取輸入源的具體狀態和屬性。
- 在擴增實境和虛擬實境環境中實現更流暢的互動。

### 使用方式
XRInputSourceEvent 的使用通常是在 XR 會話中進行事件監聽，例如：

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log('新輸入源:', inputSource);
        });
    });
});
```

在這段代碼中，當新的輸入源被添加到會話中時，將會顯示該輸入源的詳細信息。

### 詳細說明
XRInputSourceEvent 包含多個屬性，主要有：
- `inputSource`: 表示觸發事件的輸入源。
- `added`: 新增的輸入源數組。
- `removed`: 移除的輸入源數組。

這些屬性使開發者能夠更清晰地了解當前的輸入狀態。

## 範例
以下是一個基本的使用範例，展示如何監聽 XRInputSourceEvent 事件：

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log(`新輸入源 ID: ${inputSource.id}`);
        });
        
        event.removed.forEach((inputSource) => {
            console.log(`移除輸入源 ID: ${inputSource.id}`);
        });
    });
});
```

在這個範例中，當新的輸入源被添加或移除時，將會在控制台中顯示其 ID。

## 解釋
使用 XRInputSourceEvent 時，開發者需注意以下幾個常見問題：
- 確保 XR 會話已經正確啟動，否則事件將無法觸發。
- 在不同的設備上，輸入源的行為可能會有所不同，因此測試時應考慮多種設備。
- 事件的觸發可能會受到性能影響，為避免過多事件導致性能下降，建議使用節流技術。

## 一句總結
XRInputSourceEvent 是 JavaScript 中用於處理擴增實境和虛擬實境輸入源狀態變更的重要事件。