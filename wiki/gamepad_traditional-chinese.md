<!--
Meta Description: # JavaScript 遊戲手把 (Gamepad) API 完全指南 ## 概述 JavaScript 遊戲手把 API 允許開發人員在網頁上訪問並使用遊戲手把的功能，提供更沉浸的互動體驗。 ## 文檔 ### 目的 遊戲手把 API 使開發者能夠輕鬆地檢測和使用連接到電腦或移動設備的遊戲手把。...
Meta Keywords: api, gamepad, javascript, 遊戲手把, navigator
-->

# JavaScript 遊戲手把 (Gamepad) API 完全指南

## 概述
JavaScript 遊戲手把 API 允許開發人員在網頁上訪問並使用遊戲手把的功能，提供更沉浸的互動體驗。

## 文檔
### 目的
遊戲手把 API 使開發者能夠輕鬆地檢測和使用連接到電腦或移動設備的遊戲手把。這個 API 主要為了提升網頁遊戲的互動性和可玩性。

### 使用方式
要使用遊戲手把 API，開發者需先確認瀏覽器是否支援此功能，然後監聽手把連接和斷開事件，並在遊戲循環中讀取手把的按鈕和搖桿狀態。

### 主要屬性和方法
- `navigator.getGamepads()`: 返回一個包含所有連接手把的陣列。
- `Gamepad` 物件: 提供關於手把的詳細資訊，例如：
  - `id`: 手把的識別字串。
  - `buttons`: 按鈕的狀態。
  - `axes`: 搖桿的狀態。

## 範例
### 基本用法
```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("遊戲手把已連接:", event.gamepad.id);
});

function update() {
    const gamepads = navigator.getGamepads();
    if (gamepads[0]) {
        const gamepad = gamepads[0];
        console.log("按鈕狀態:", gamepad.buttons.map(button => button.pressed));
        console.log("搖桿狀態:", gamepad.axes);
    }
    requestAnimationFrame(update);
}

update();
```

## 解釋
### 常見的陷阱
1. **瀏覽器支援性**: 並非所有瀏覽器均支援遊戲手把 API。開發者應先檢查當前瀏覽器的相容性。
2. **事件處理**: 必須正確監聽 `gamepadconnected` 和 `gamepaddisconnected` 事件，以便追踪手把的狀態。
3. **更新循環**: 需在遊戲循環中定期呼叫 `navigator.getGamepads()` 以獲取最新的手把數據。

### 額外注意事項
- 某些手把可能會使用不同的按鈕映射，開發者應該熟悉所使用手把的具體配置。
- 對於複雜的遊戲，可能需要處理多個手把的狀態。

## 單行總結
JavaScript 遊戲手把 API 允許開發者輕鬆地在網頁中集成遊戲手把功能，提升遊戲的互動性。