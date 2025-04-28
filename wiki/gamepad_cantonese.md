<!--
Meta Description: # JavaScript 遊戲手掣 (Gamepad) API 詳細指南 ## 概述 JavaScript 的遊戲手掣 (Gamepad) API 允許開發者輕鬆訪問和使用遊戲手掣的功能，這使得在網頁應用程式中整合遊戲控制變得簡單。 ## 文檔 ### 目的 遊戲手掣 API 旨在提供一個標準化的方...
Meta Keywords: api, javascript, gamepads, 遊戲手掣, navigator
-->

# JavaScript 遊戲手掣 (Gamepad) API 詳細指南

## 概述
JavaScript 的遊戲手掣 (Gamepad) API 允許開發者輕鬆訪問和使用遊戲手掣的功能，這使得在網頁應用程式中整合遊戲控制變得簡單。

## 文檔
### 目的
遊戲手掣 API 旨在提供一個標準化的方式來檢測和使用連接到用戶設備上的遊戲手掣。這使得開發者能夠開發互動式遊戲和應用，利用外部控制器的輸入。

### 使用方法
要使用遊戲手掣 API，首先需要檢查瀏覽器的支持情況，然後可以使用 `navigator.getGamepads()` 方法來獲取當前連接的遊戲手掣的狀態。

#### 主要方法和屬性：
- `navigator.getGamepads()`: 返回一個包含當前連接的所有遊戲手掣的數組。
- `Gamepad`: 包含遊戲手掣的屬性，例如 `id`、`index`、`buttons` 和 `axes`。

### 詳細說明
遊戲手掣 API 的設計是為了在不同平台上提供一致的使用體驗。開發者可以通過以下步驟來實現基本的遊戲手掣功能：

1. **檢查支持情況**：
   ```javascript
   if ("getGamepads" in navigator) {
       console.log("遊戲手掣 API 支持");
   } else {
       console.log("遊戲手掣 API 不支持");
   }
   ```

2. **獲取遊戲手掣狀態**：
   ```javascript
   const gamepads = navigator.getGamepads();
   ```

3. **檢查特定遊戲手掣的按鈕和軸狀態**：
   ```javascript
   if (gamepads[0]) {
       const buttons = gamepads[0].buttons;
       const axes = gamepads[0].axes;
       console.log(buttons, axes);
   }
   ```

## 範例
以下是一個簡單的範例，展示如何使用遊戲手掣 API 來檢測按鈕按下的情況：

```javascript
function updateGamepadStatus() {
    const gamepads = navigator.getGamepads();
    if (gamepads[0]) {
        const buttonA = gamepads[0].buttons[0].pressed; // 假設第一個按鈕是 A 按鈕
        if (buttonA) {
            console.log("按下了 A 按鈕");
        }
    }
    requestAnimationFrame(updateGamepadStatus);
}

requestAnimationFrame(updateGamepadStatus);
```

## 解釋
使用遊戲手掣 API 時，開發者需要注意以下幾點：
- 瀏覽器支持：並非所有瀏覽器都支持遊戲手掣 API，因此需要檢查支持狀況。
- 按鈕和軸的索引：按鈕和軸的索引可能因不同的控制器而異，因此在開發時應進行測試。
- 更新頻率：監聽遊戲手掣狀態的更新需要使用 `requestAnimationFrame` 或定時器，以確保流暢的使用體驗。

## 總結
JavaScript 的遊戲手掣 API 使開發者能夠輕鬆地集成和使用遊戲手掣，為網頁應用程式帶來更好的互動性和遊戲體驗。