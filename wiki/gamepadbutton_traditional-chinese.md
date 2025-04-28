<!--
Meta Description: # GamepadButton：JavaScript 中的遊戲手柄按鈕 ## 簡介 `GamepadButton` 是一個用於操控遊戲手柄按鈕的 JavaScript 介面，能夠讓開發者在網頁應用中輕鬆檢測和使用遊戲手柄的按鈕。 ## 文檔 ### 目的 `GamepadButton` 介面主要用於...
Meta Keywords: gamepadbutton, gamepad, javascript, getgamepads, console
-->

# GamepadButton：JavaScript 中的遊戲手柄按鈕

## 簡介
`GamepadButton` 是一個用於操控遊戲手柄按鈕的 JavaScript 介面，能夠讓開發者在網頁應用中輕鬆檢測和使用遊戲手柄的按鈕。

## 文檔
### 目的
`GamepadButton` 介面主要用於表示遊戲手柄上的單個按鈕，提供有關按鈕狀態（如是否被按下或釋放）及其壓力的資訊。

### 使用方法
在 JavaScript 中，`GamepadButton` 物件通常是透過 `Gamepad` 介面獲得，開發者可以使用 `navigator.getGamepads()` 方法來檢索連接的遊戲手柄及其所有按鈕的狀態。

### 詳細說明
- **屬性**
  - `pressed`：一個布林值，指示該按鈕當前是否被按下。
  - `value`：一個數字，表示按鈕的壓力值，範圍從 0 到 1，0 表示未按下，1 表示完全按下。

- **方法**：`GamepadButton` 本身並不提供方法，但可以通過 `Gamepad` 介面進行查詢。

### 例子
以下是使用 `GamepadButton` 的基本範例：

```javascript
window.addEventListener("gamepadconnected", (event) => {
    console.log("遊戲手柄已連接！");
    
    const gamepad = navigator.getGamepads()[event.gamepad.index];
    
    // 檢查第一個按鈕的狀態
    const button = gamepad.buttons[0];
    console.log(`按鈕是否被按下：${button.pressed}`);
    console.log(`按鈕壓力值：${button.value}`);
});

window.addEventListener("gamepaddisconnected", (event) => {
    console.log("遊戲手柄已斷開！");
});
```

## 解釋
在使用 `GamepadButton` 時，有幾個常見的陷阱：
- 確保在使用 `navigator.getGamepads()` 前，遊戲手柄已正確連接，否則將返回 `undefined`。
- `pressed` 屬性在快速連按時可能會出現延遲，因此在遊戲中需要考慮這一點。
- 當檢查按鈕狀態時，應該在每次循環中查詢 `getGamepads()`，因為按鈕狀態會隨時間變化。

## 總結
`GamepadButton` 是一個強大的工具，能幫助開發者輕鬆地處理遊戲手柄按鈕的狀態，增強用戶互動體驗。