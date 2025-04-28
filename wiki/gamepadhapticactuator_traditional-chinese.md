<!--
Meta Description: # GamepadHapticActuator：JavaScript中的遊戲控制器觸覺反饋 ## 概述 `GamepadHapticActuator` 是一個JavaScript API，用於控制遊戲控制器的觸覺反饋功能，讓開發者能夠為用戶提供更具沉浸感的遊戲體驗。 ## 文檔 `GamepadHa...
Meta Keywords: gamepadhapticactuator, gamepad, pulses, const, console
-->

# GamepadHapticActuator：JavaScript中的遊戲控制器觸覺反饋

## 概述
`GamepadHapticActuator` 是一個JavaScript API，用於控制遊戲控制器的觸覺反饋功能，讓開發者能夠為用戶提供更具沉浸感的遊戲體驗。

## 文檔
`GamepadHapticActuator` 主要用於為支持觸覺反饋的遊戲控制器提供震動效果。這一API的出現使得開發者能夠不僅依賴視覺和聽覺，還能利用觸覺來增強互動性。

### 目的
透過 `GamepadHapticActuator`，開發者可以使用 JavaScript 控制連接的遊戲控制器的震動功能，這有助於增強遊戲的沉浸感和反應性。

### 使用方法
要使用 `GamepadHapticActuator`，首先需要檢查遊戲控制器是否支持該功能，然後設置震動效果。

### 詳細信息
- **屬性**：
  - **`pulses`**: 一個數組，包含了震動的強度和持續時間。
- **方法**：
  - **`playEffect(type, options)`**: 播放觸覺效果，`type`可為不同震動效果的類型，`options`包含震動的參數設置。

## 範例
以下是使用 `GamepadHapticActuator` 的基本範例：

```javascript
// 確保瀏覽器支持 Gamepad API
if ('getGamepads' in navigator) {
    const gamepads = navigator.getGamepads();
    const gamepad = gamepads[0]; // 獲取第一個連接的遊戲控制器

    if (gamepad && gamepad.hapticActuators.length > 0) {
        const actuator = gamepad.hapticActuators[0]; // 獲取第一個觸覺反饋裝置
        const pulses = [{ duration: 1000, strength: 1.0 }]; // 設置震動參數

        actuator.playEffect('custom', { duration: 2000, pulses: pulses })
            .then(() => console.log('震動效果已啟動'))
            .catch((error) => console.error('震動效果播放失敗:', error));
    } else {
        console.log('該控制器不支持觸覺反饋');
    }
}
```

## 解釋
在使用 `GamepadHapticActuator` 時，開發者應注意以下幾點：
- 並非所有控制器都支持觸覺反饋，因此在使用前應進行檢查。
- 震動效果的強度和持續時間可能會因控制器型號而異，建議進行測試以確保效果符合預期。
- 部分瀏覽器對 `GamepadHapticActuator` 的支持可能不完整，開發者應確認其兼容性。

## 總結
`GamepadHapticActuator` 為JavaScript開發者提供了一種新的方式來增強遊戲體驗，透過觸覺反饋提升用戶互動。