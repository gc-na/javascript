<!--
Meta Description: # RelativeOrientationSensor: JavaScript 中的相對方向感應器 ## 摘要 RelativeOrientationSensor 是一個能夠提供設備相對於其初始方向的三維方向數據的 Web API，主要用於增強現實（AR）和虛擬現實（VR）應用程式。 ## 文檔 R...
Meta Keywords: relativeorientationsensor, sensor, quaternion, console, javascript
-->

# RelativeOrientationSensor: JavaScript 中的相對方向感應器

## 摘要
RelativeOrientationSensor 是一個能夠提供設備相對於其初始方向的三維方向數據的 Web API，主要用於增強現實（AR）和虛擬現實（VR）應用程式。

## 文檔
RelativeOrientationSensor 是一種感應器，允許開發者獲取設備的方向數據，這些數據相對於設備的初始方向。它利用設備的陀螺儀和加速度計來計算相對方向。這對於需要精確追踪設備方向的應用非常重要，比如 AR 和 VR 應用。

### 目的
RelativeOrientationSensor 旨在提供一種簡單的方法來獲取設備的方向數據，並能夠用於各種互動式和沉浸式體驗。

### 使用方法
要使用 RelativeOrientationSensor，首先需要檢查瀏覽器是否支持該功能。然後可以創建一個新的 RelativeOrientationSensor 實例，並通過監聽其 `reading` 事件來獲取方向數據。

#### 基本語法
```javascript
if ('RelativeOrientationSensor' in window) {
  const sensor = new RelativeOrientationSensor();
  sensor.start();

  sensor.addEventListener('reading', () => {
    console.log(`X: ${sensor.quaternion[0]}, Y: ${sensor.quaternion[1]}, Z: ${sensor.quaternion[2]}, W: ${sensor.quaternion[3]}`);
  });
} else {
  console.error('RelativeOrientationSensor is not supported in this browser.');
}
```

## 範例
以下是使用 RelativeOrientationSensor 的基本範例：

### 簡單範例
```javascript
if ('RelativeOrientationSensor' in window) {
  const sensor = new RelativeOrientationSensor({frequency: 60});
  sensor.start();

  sensor.addEventListener('reading', () => {
    console.log(`當前方向: ${sensor.quaternion}`);
  });
} else {
  console.log('此瀏覽器不支持 RelativeOrientationSensor。');
}
```

### 進階範例
```javascript
if ('RelativeOrientationSensor' in window) {
  const sensor = new RelativeOrientationSensor({
    frequency: 30,
    referenceFrame: 'screen'
  });
  sensor.start();

  sensor.addEventListener('reading', () => {
    const { quaternion } = sensor;
    // 使用 quaternion 數據更新場景方向
    updateSceneDirection(quaternion);
  });

  function updateSceneDirection(quaternion) {
    // 更新場景的方向邏輯
  }
} else {
  console.log('此瀏覽器不支持 RelativeOrientationSensor。');
}
```

## 解釋
使用 RelativeOrientationSensor 時需注意以下幾點：

- **瀏覽器支持**：並非所有瀏覽器都支持 RelativeOrientationSensor，請務必進行檢查。
- **權限問題**：某些瀏覽器可能需要用戶授予權限才能使用設備感應器。
- **性能考量**：高頻率的讀取可能會影響設備性能，因此應根據應用需求調整頻率。

## 一句總結
RelativeOrientationSensor 是一個強大的 Web API，能夠提供設備相對方向數據，適用於增強現實和虛擬現實應用。