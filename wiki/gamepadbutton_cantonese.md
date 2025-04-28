<!--
Meta Description: # JavaScript 中的 GamepadButton：完整指南 ## 概覽 GamepadButton 是一個 JavaScript 接口，讓開發者可以讀取遊戲控制器按鈕的狀態。這個功能對於遊戲開發者來說非常重要，因為它允許他們輕鬆集成遊戲控制器的支持，增強用戶體驗。 ## 文檔 ### 目的...
Meta Keywords: gamepadbutton, javascript, gamepads, button, gamepad
-->

# JavaScript 中的 GamepadButton：完整指南

## 概覽
GamepadButton 是一個 JavaScript 接口，讓開發者可以讀取遊戲控制器按鈕的狀態。這個功能對於遊戲開發者來說非常重要，因為它允許他們輕鬆集成遊戲控制器的支持，增強用戶體驗。

## 文檔
### 目的
GamepadButton 主要用於訪問遊戲控制器按鈕的屬性，幫助開發者獲取按鈕的狀態（按下或釋放）和壓力感應值。

### 使用方法
在 JavaScript 中，GamepadButton 對象通常與 Gamepad API 共同使用。你可以通過 `navigator.getGamepads()` 方法獲取當前連接的遊戲控制器，然後檢查每個按鈕的狀態。

### 屬性
- `pressed`：布林值，表示按鈕是否被按下。
- `value`：數值，表示按鈕的壓力感應值（範圍從 0 到 1）。

### 示例
```javascript
// 獲取遊戲控制器
const gamepads = navigator.getGamepads();

// 檢查第一個控制器的按鈕狀態
if (gamepads[0]) {
    const button = gamepads[0].buttons[0]; // 獲取第一個按鈕
    if (button.pressed) {
        console.log("第一個按鈕被按下！");
    }
    console.log("按鈕壓力值:", button.value);
}
```

## 解釋
在使用 GamepadButton 時，開發者需要注意以下幾點：
1. **相容性**：並非所有瀏覽器都支持 Gamepad API，因此在使用之前應進行相容性檢查。
2. **更新狀態**：遊戲控制器的狀態需要在每次更新循環中檢查，因為按鈕狀態是即時變化的。
3. **使用者授權**：某些瀏覽器可能需要用戶的操作（例如點擊）以啟用遊戲控制器的支持。

## 一句總結
GamepadButton 是 JavaScript 中用於檢測遊戲控制器按鈕狀態的重要接口，對於提升遊戲互動性至關重要。