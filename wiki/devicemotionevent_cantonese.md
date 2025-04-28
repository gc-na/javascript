<!--
Meta Description: # DeviceMotionEvent：JavaScript 中的設備運動事件 ## 概述 `DeviceMotionEvent` 是一個在 JavaScript 中使用的事件，允許開發者訪問設備的運動數據，包括加速度、旋轉速率和設備的方向。這使得開發者能夠創建基於設備運動的互動應用程式。 ## 文...
Meta Keywords: event, devicemotionevent, javascript, acceleration, rotationrate
-->

# DeviceMotionEvent：JavaScript 中的設備運動事件

## 概述
`DeviceMotionEvent` 是一個在 JavaScript 中使用的事件，允許開發者訪問設備的運動數據，包括加速度、旋轉速率和設備的方向。這使得開發者能夠創建基於設備運動的互動應用程式。

## 文檔
### 目的
`DeviceMotionEvent` 用於捕捉設備的運動資訊，這對於開發例如遊戲、健身應用或其他需要實時運動監測的應用程式非常重要。

### 使用方式
要使用 `DeviceMotionEvent`，開發者需要監聽該事件，然後從事件對象中提取所需的運動數據。

#### 基本語法：
```javascript
window.addEventListener('devicemotion', function(event) {
    var acceleration = event.acceleration; // 加速度
    var rotationRate = event.rotationRate; // 旋轉速率
    var accelerationIncludingGravity = event.accelerationIncludingGravity; // 包含重力的加速度
    // 進行相應的處理
});
```

### 事件屬性
- `acceleration`：表示設備的加速度（以 m/s² 為單位）。
- `accelerationIncludingGravity`：表示設備的加速度，包括重力影響。
- `rotationRate`：表示設備的旋轉速率（以度/秒為單位）。

## 示例
以下是使用 `DeviceMotionEvent` 的基本示例：

### 示例 1：顯示加速度數據
```javascript
window.addEventListener('devicemotion', function(event) {
    console.log('X 軸加速度:', event.acceleration.x);
    console.log('Y 軸加速度:', event.acceleration.y);
    console.log('Z 軸加速度:', event.acceleration.z);
});
```

### 示例 2：顯示旋轉速率
```javascript
window.addEventListener('devicemotion', function(event) {
    console.log('X 軸旋轉速率:', event.rotationRate.alpha);
    console.log('Y 軸旋轉速率:', event.rotationRate.beta);
    console.log('Z 軸旋轉速率:', event.rotationRate.gamma);
});
```

## 解釋
在使用 `DeviceMotionEvent` 時，開發者需要注意以下幾個常見問題：

1. **隱私權要求**：某些瀏覽器（如 Safari）可能需要用戶授權才能訪問運動數據。開發者應確保在請求權限時提供清晰的說明。

2. **設備兼容性**：並非所有設備都支持 `DeviceMotionEvent`，開發者應檢查用戶的設備兼容性。

3. **事件頻率**：事件的觸發頻率可能因設備而異，開發者應考慮這一點以確保應用的性能。

## 總結
`DeviceMotionEvent` 允許 JavaScript 開發者獲取設備的運動數據，從而創建互動性強的應用程式。