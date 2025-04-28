<!--
Meta Description: # JavaScript OrientationSensor 介紹：使用 JavaScript 獲取裝置方向 ## 概述 OrientationSensor 是一個用於獲取設備方向的 Web API，允許開發者在其應用程式中使用設備的方向數據來創建互動式體驗。這對於遊戲開發、虛擬實境應用以及各種需要...
Meta Keywords: orientationsensor, sensor, javascript, console, log
-->

# JavaScript OrientationSensor 介紹：使用 JavaScript 獲取裝置方向

## 概述
OrientationSensor 是一個用於獲取設備方向的 Web API，允許開發者在其應用程式中使用設備的方向數據來創建互動式體驗。這對於遊戲開發、虛擬實境應用以及各種需要設備姿態的場景非常有用。

## 文檔
### 目的
OrientationSensor 提供了一個簡單的方式來訪問設備的方向數據，包括設備的朝向和旋轉。這對於開發者來說，可以用來增強用戶體驗，例如在移動設備上實現基於方向的控制。

### 使用方法
要使用 OrientationSensor，您需要創建一個新的 OrientationSensor 實例，然後監聽其事件以獲取方向數據。以下是基本的步驟：

1. **創建 OrientationSensor 實例**
   ```javascript
   const sensor = new OrientationSensor();
   ```

2. **啟動感應器**
   ```javascript
   sensor.start();
   ```

3. **監聽事件**
   ```javascript
   sensor.addEventListener('reading', () => {
       console.log(`Alpha: ${sensor.alpha}`);
       console.log(`Beta: ${sensor.beta}`);
       console.log(`Gamma: ${sensor.gamma}`);
   });
   ```

4. **停止感應器**
   ```javascript
   sensor.stop();
   ```

### 詳細說明
OrientationSensor 提供了以下屬性：
- `alpha`: 設備繞 Z 軸的旋轉角度（以度為單位）。
- `beta`: 設備繞 X 軸的旋轉角度（以度為單位）。
- `gamma`: 設備繞 Y 軸的旋轉角度（以度為單位）。

此外，使用 OrientationSensor 需要注意以下幾點：
- 使用此 API 需要 HTTPS 或 localhost 環境。
- 確保用戶授予了訪問設備方向的權限。

## 示例
以下是使用 OrientationSensor 的基本範例：

```javascript
if ('OrientationSensor' in window) {
    const sensor = new OrientationSensor({ frequency: 60 });

    sensor.addEventListener('reading', () => {
        console.log(`Alpha: ${sensor.alpha}`);
        console.log(`Beta: ${sensor.beta}`);
        console.log(`Gamma: ${sensor.gamma}`);
    });

    sensor.start();
} else {
    console.log('此設備不支持 OrientationSensor。');
}
```

## 說明
在使用 OrientationSensor 時，開發者應注意以下常見問題：
- **權限問題**：在某些瀏覽器中，必須獲得用戶的明確許可才能訪問傳感器數據。
- **性能考量**：持續監聽傳感器數據可能會影響應用程式的性能，因此應根據需要啟動和停止感應器。
- **設備兼容性**：並非所有設備都支持此 API，因此在實現時應考慮備用方案。

## 簡要總結
OrientationSensor 是一個強大的工具，讓開發者能夠在 JavaScript 中獲取設備的方向數據，為用戶提供更具互動性的體驗。