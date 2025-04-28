<!--
Meta Description: # DeviceMotionEventRotationRate 在 JavaScript 中的應用 ## 概述 `DeviceMotionEventRotationRate` 是一個與設備運動相關的事件，提供設備在三個軸上的旋轉速率資訊。這個特性對於開發需要感應器數據的應用程式（如遊戲、增強實境等）...
Meta Keywords: rotationrate, devicemotioneventrotationrate, alpha, beta, gamma
-->

# DeviceMotionEventRotationRate 在 JavaScript 中的應用

## 概述
`DeviceMotionEventRotationRate` 是一個與設備運動相關的事件，提供設備在三個軸上的旋轉速率資訊。這個特性對於開發需要感應器數據的應用程式（如遊戲、增強實境等）特別有用。

## 文檔
### 目的
`DeviceMotionEventRotationRate` 用於獲取設備在 X、Y 和 Z 軸上的旋轉速率，以度每秒（degrees per second）為單位。這些數據可以用來檢測設備的旋轉動作，幫助開發者創建更互動的用戶體驗。

### 使用方法
要使用 `DeviceMotionEventRotationRate`，首先需要確保用戶的設備支持設備運動事件。接著，開發者可以監聽 `devicemotion` 事件，並從事件對象中獲取 `rotationRate` 屬性。

### 詳細說明
```javascript
window.addEventListener('devicemotion', function(event) {
    const rotationRate = event.rotationRate;
    console.log('X 軸旋轉速率:', rotationRate.alpha);
    console.log('Y 軸旋轉速率:', rotationRate.beta);
    console.log('Z 軸旋轉速率:', rotationRate.gamma);
});
```

- **rotationRate.alpha**: 表示 Z 軸的旋轉速率。
- **rotationRate.beta**: 表示 X 軸的旋轉速率。
- **rotationRate.gamma**: 表示 Y 軸的旋轉速率。

## 範例
以下是如何使用 `DeviceMotionEventRotationRate` 的基本範例：

```javascript
window.addEventListener('devicemotion', function(event) {
    const { alpha, beta, gamma } = event.rotationRate;
    console.log(`旋轉速率 - Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
});
```

在這個範例中，當設備運動時，將會在控制台中輸出旋轉速率。

## 說明
### 常見問題
- **設備支持性**: 並不是所有設備都支持設備運動事件，因此在使用之前，開發者應檢查設備是否支持。
- **權限要求**: 在某些瀏覽器中，使用設備運動事件可能需要用戶授權，特別是在行動設備上。
- **數據準確性**: 旋轉速率的數據可能會受到設備的硬體限制影響，因此開發者應考慮這一點。

## 一句總結
`DeviceMotionEventRotationRate` 提供設備旋轉速率的資訊，幫助開發者創建更具互動性的應用程式。