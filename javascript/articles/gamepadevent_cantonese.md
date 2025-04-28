<!--
Meta Description: # GamepadEvent 事件：JavaScript 遊戲手掣事件詳解 ## 概要 `GamepadEvent` 是一個用於處理遊戲手掣互動的事件，讓開發者可以輕鬆地獲取遊戲手掣的按鈕和軸位資料，從而增強網頁遊戲的互動性。 ## 文檔 `GamepadEvent` 事件是由瀏覽器在遊戲手掣狀態改...
Meta Keywords: gamepadevent, event, window, gamepad, javascript
-->

# GamepadEvent 事件：JavaScript 遊戲手掣事件詳解

## 概要
`GamepadEvent` 是一個用於處理遊戲手掣互動的事件，讓開發者可以輕鬆地獲取遊戲手掣的按鈕和軸位資料，從而增強網頁遊戲的互動性。

## 文檔
`GamepadEvent` 事件是由瀏覽器在遊戲手掣狀態改變時觸發的。它包含了有關手掣的詳細信息，開發者可以利用這些信息來設計互動式遊戲或應用程式。`GamepadEvent` 主要有兩個事件類型：`gamepadconnected` 和 `gamepaddisconnected`。

### 目的
- 監測遊戲手掣的連接和斷開。
- 獲取手掣的按鈕和軸位狀態。

### 使用方法
要使用 `GamepadEvent`，開發者需為 `window` 對象添加事件監聽器，如下所示：

```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("遊戲手掣已連接:", event.gamepad);
});

window.addEventListener("gamepaddisconnected", function(event) {
    console.log("遊戲手掣已斷開:", event.gamepad);
});
```

## 示例
以下是使用 `GamepadEvent` 的基本示例：

### 連接遊戲手掣
```javascript
window.addEventListener("gamepadconnected", function(event) {
    alert("遊戲手掣連接！手掣 ID: " + event.gamepad.id);
});
```

### 斷開遊戲手掣
```javascript
window.addEventListener("gamepaddisconnected", function(event) {
    alert("遊戲手掣斷開！手掣 ID: " + event.gamepad.id);
});
```

## 解釋
在使用 `GamepadEvent` 時，開發者需注意以下幾點：

1. **瀏覽器支持**：並非所有瀏覽器都支持 `Gamepad API`，請在開發前確認目標瀏覽器的兼容性。
2. **用戶許可**：某些瀏覽器可能需要用戶的許可才能使用遊戲手掣功能。
3. **性能考慮**：頻繁地檢查遊戲手掣的狀態可能會影響性能，建議在遊戲主循環中適度使用。

## 一句總結
`GamepadEvent` 是一個強大的工具，能夠讓開發者輕鬆處理遊戲手掣的連接和狀態變化。