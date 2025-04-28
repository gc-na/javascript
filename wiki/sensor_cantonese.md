<!--
Meta Description: # JavaScript 中的傳感器 (Sensor) ## 概述 JavaScript 的傳感器 API 允許開發者訪問設備的各種傳感器數據，如加速度計、陀螺儀、地磁儀等，從而使網頁應用程序能夠與物理環境互動，增強用戶體驗。 ## 文檔 ### 目的 傳感器 API 旨在提供設備的實時數據，這些數...
Meta Keywords: accelerometer, gyroscope, javascript, console, log
-->

# JavaScript 中的傳感器 (Sensor)

## 概述
JavaScript 的傳感器 API 允許開發者訪問設備的各種傳感器數據，如加速度計、陀螺儀、地磁儀等，從而使網頁應用程序能夠與物理環境互動，增強用戶體驗。

## 文檔
### 目的
傳感器 API 旨在提供設備的實時數據，這些數據可以用於創建具有增強現實、遊戲或其他互動體驗的應用程序。這些數據包括但不限於設備的運動、方向和位置。

### 使用方法
要使用傳感器 API，開發者需要首先檢查用戶的瀏覽器是否支持相應的傳感器，然後可以通過建立一個傳感器實例來訪問數據。

常用的傳感器包括：
- **加速度計 (Accelerometer)**: 測量設備的加速度。
- **陀螺儀 (Gyroscope)**: 測量設備的角速度。
- **地磁儀 (Magnetometer)**: 測量設備的磁場。

以下是基本的使用示例：

```javascript
if ('Accelerometer' in window) {
    let accelerometer = new Accelerometer({frequency: 60});
    accelerometer.start();

    accelerometer.addEventListener('reading', () => {
        console.log(`加速度 - x: ${accelerometer.x}, y: ${accelerometer.y}, z: ${accelerometer.z}`);
    });
} else {
    console.log('您的瀏覽器不支持加速度計。');
}
```

## 範例
### 加速度計使用示例
```javascript
if ('Accelerometer' in window) {
    const accelerometer = new Accelerometer({frequency: 30});
    accelerometer.start();

    accelerometer.addEventListener('reading', () => {
        console.log(`加速度 - x: ${accelerometer.x}, y: ${accelerometer.y}, z: ${accelerometer.z}`);
    });
} else {
    console.log('加速度計不被支持');
}
```

### 陀螺儀使用示例
```javascript
if ('Gyroscope' in window) {
    const gyroscope = new Gyroscope({frequency: 30});
    gyroscope.start();

    gyroscope.addEventListener('reading', () => {
        console.log(`角速度 - alpha: ${gyroscope.alpha}, beta: ${gyroscope.beta}, gamma: ${gyroscope.gamma}`);
    });
} else {
    console.log('陀螺儀不被支持');
}
```

## 解釋
在使用傳感器 API 時，開發者需要注意以下幾點：
1. **權限問題**: 許多傳感器需要用戶授予權限才能使用。確保在應用中處理這些權限請求。
2. **設備支持**: 並非所有設備都支持所有傳感器，因此在使用之前檢查支持情況是非常重要的。
3. **性能考量**: 傳感器數據的頻率可能會影響應用的性能，尤其是在高頻數據流的情況下。

## 一句總結
JavaScript 的傳感器 API 提供實時訪問設備的傳感器數據，增強了網頁應用的互動性。