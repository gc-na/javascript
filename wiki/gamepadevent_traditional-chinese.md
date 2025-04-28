<!--
Meta Description: # GamepadEvent: JavaScript中的遊戲手把事件 ## 概述 `GamepadEvent` 是一種用於在網頁應用程式中處理遊戲手把的事件。它使開發者能夠監聽並響應遊戲手把的輸入，為用戶提供更流暢的遊戲體驗。 ## 文檔 `GamepadEvent` 是一個事件物件，當遊戲手把的狀...
Meta Keywords: event, gamepadevent, gamepad, gamepadconnected, window
-->

# GamepadEvent: JavaScript中的遊戲手把事件

## 概述
`GamepadEvent` 是一種用於在網頁應用程式中處理遊戲手把的事件。它使開發者能夠監聽並響應遊戲手把的輸入，為用戶提供更流暢的遊戲體驗。

## 文檔
`GamepadEvent` 是一個事件物件，當遊戲手把的狀態改變時被觸發。它提供了有關當前連接的遊戲手把及其按鈕和軸的詳細資訊。這個事件通常與 `gamepadconnected` 和 `gamepaddisconnected` 事件一起使用，來管理遊戲手把的連接狀態。

### 目的
`GamepadEvent` 的主要目的在於：
- 監測遊戲手把的連接和斷開。
- 獲取手把的狀態（按鈕和軸的輸入）。

### 使用方式
開發者可以使用下列方式來監聽 `GamepadEvent`：

```javascript
window.addEventListener("gamepadconnected", (event) => {
    console.log("遊戲手把已連接:", event.gamepad);
});

window.addEventListener("gamepaddisconnected", (event) => {
    console.log("遊戲手把已斷開:", event.gamepad);
});
```

## 範例
以下是如何使用 `GamepadEvent` 監聽遊戲手把的連接和斷開的基本範例：

```javascript
// 監聽遊戲手把連接事件
window.addEventListener("gamepadconnected", (event) => {
    console.log(`手把 ${event.gamepad.index} 連接成功！`);
});

// 監聽遊戲手把斷開事件
window.addEventListener("gamepaddisconnected", (event) => {
    console.log(`手把 ${event.gamepad.index} 已斷開！`);
});
```

## 解釋
在使用 `GamepadEvent` 時，開發者應注意以下幾點：
- **兼容性**：並非所有瀏覽器都支持遊戲手把 API，因此在使用之前請確認目標瀏覽器的兼容性。
- **事件觸發**：`gamepadconnected` 事件僅在遊戲手把實際連接時觸發，必須確保手把已正確連接才能接收到該事件。
- **對應的遊戲手把**：`event.gamepad` 包含了手把的詳細信息，包括按鈕和軸的狀態，可以通過這些信息進行更進一步的事件處理。

## 一行總結
`GamepadEvent` 提供了遊戲手把的連接與斷開監聽功能，幫助開發者創建更具互動性的網頁遊戲體驗。