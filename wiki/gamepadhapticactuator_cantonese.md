<!--
Meta Description: # GamepadHapticActuator: JavaScript中的遊戲手掣觸感執行器 ## 簡介 `GamepadHapticActuator` 係一個用於 JavaScript 嘅 API，允許開發者透過遊戲手掣提供觸感反饋。呢個功能可以提升遊戲體驗，讓玩家感受到更真實嘅互動。 ## 文檔...
Meta Keywords: gamepadhapticactuator, gamepad, javascript, let, api
-->

# GamepadHapticActuator: JavaScript中的遊戲手掣觸感執行器

## 簡介
`GamepadHapticActuator` 係一個用於 JavaScript 嘅 API，允許開發者透過遊戲手掣提供觸感反饋。呢個功能可以提升遊戲體驗，讓玩家感受到更真實嘅互動。

## 文檔
### 目的
`GamepadHapticActuator` 主要用於提供觸感反饋，通常用於遊戲開發中。開發者可以利用呢個 API 來控制手掣嘅震動和其他觸感效果，增強玩家嘅沉浸感。

### 用法
要使用 `GamepadHapticActuator`，首先必須檢查遊戲手掣是否支持觸感反饋。當手掣連接到設備後，可以用以下方法訪問觸感執行器：

```javascript
let gamepads = navigator.getGamepads();
let gamepad = gamepads[0]; // 假設使用第一個遊戲手掣

if (gamepad.hapticActuators.length > 0) {
    let hapticActuator = gamepad.hapticActuators[0];
    // 使用 hapticActuator 來控制觸感反饋
}
```

### 詳細信息
每個 `GamepadHapticActuator` 對象都擁有以下屬性和方法：

- **pulse(value, duration)**: 此方法會讓觸感執行器產生一個脈衝效果。`value` 代表觸感強度（範圍通常是 0 到 1），`duration` 代表持續時間（毫秒）。
  
範例：

```javascript
hapticActuator.pulse(1.0, 1000); // 強度最大，持續 1 秒
```

## 範例
下面係一個簡單的範例，展示如何使用 `GamepadHapticActuator` 來提供觸感反饋：

```javascript
window.addEventListener("gamepadconnected", function(event) {
    let gamepad = event.gamepad;
    let actuator = gamepad.hapticActuators[0];

    if (actuator) {
        actuator.pulse(0.5, 500); // 中等強度，持續 0.5 秒
    }
});
```

## 解釋
使用 `GamepadHapticActuator` 時需要注意以下幾點：

- **兼容性**: 不是所有的遊戲手掣都支持觸感反饋，開發者應該在使用之前檢查手掣是否具備此功能。
- **性能影響**: 觸感反饋可能會影響性能，尤其是在高頻率使用的情況下。適當使用可以提高遊戲體驗，但過度使用可能會導致延遲或性能下降。
- **設備差異**: 不同設備之間的觸感反饋可能會有所不同，開發者應該在多個設備上進行測試，以確保最佳的用戶體驗。

## 簡單總結
`GamepadHapticActuator` 係一個用於提供觸感反饋的 JavaScript API，能夠提升遊戲互動性和沉浸感。