<!--
Meta Description: # DeviceOrientationEvent：JavaScript 中的設備方向事件 ## 簡介 `DeviceOrientationEvent` 是一個 JavaScript 事件，允許網頁從設備的傳感器獲取方向和運動資訊，幫助開發者在應用中使用設備的方向感知功能。 ## 文檔 `Device...
Meta Keywords: deviceorientationevent, event, alpha, beta, gamma
-->

# DeviceOrientationEvent：JavaScript 中的設備方向事件

## 簡介
`DeviceOrientationEvent` 是一個 JavaScript 事件，允許網頁從設備的傳感器獲取方向和運動資訊，幫助開發者在應用中使用設備的方向感知功能。

## 文檔
`DeviceOrientationEvent` 事件通過設備的陀螺儀和加速度計提供有關設備在三維空間中的位置和運動的數據。此事件可用於創建互動性更強的應用，例如增強現實（AR）應用或遊戲。

### 目的
`DeviceOrientationEvent` 的主要目的是讓開發者可以輕鬆訪問設備的運動和方向數據，這在許多現代應用中變得越來越重要。

### 使用方法
要使用 `DeviceOrientationEvent`，首先需要檢查該事件是否受到支持。然後，可以添加事件監聽器來捕獲設備的方向變化。

```javascript
if (window.DeviceOrientationEvent) {
    window.addEventListener('deviceorientation', function(event) {
        const alpha = event.alpha; // 繞 Z 軸旋轉
        const beta = event.beta;   // 繞 X 軸旋轉
        const gamma = event.gamma; // 繞 Y 軸旋轉
        
        console.log(`Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
    }, true);
} else {
    console.log('該設備不支持 Device Orientation API。');
}
```

### 詳細說明
- **alpha**：表示設備繞 Z 軸的旋轉（以度為單位）。
- **beta**：表示設備繞 X 軸的傾斜（以度為單位）。
- **gamma**：表示設備繞 Y 軸的傾斜（以度為單位）。

這些參數的值範圍如下：
- `alpha`：0 到 360 度。
- `beta` 和 `gamma`：-180 到 180 度。

## 範例
以下是一個簡單的範例，展示如何使用 `DeviceOrientationEvent` 來顯示設備的方向數據。

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>設備方向事件示範</title>
    <script>
        window.addEventListener('deviceorientation', function(event) {
            document.getElementById('output').innerText = 
                `Alpha: ${event.alpha.toFixed(2)}\nBeta: ${event.beta.toFixed(2)}\nGamma: ${event.gamma.toFixed(2)}`;
        }, true);
    </script>
</head>
<body>
    <h1>設備方向事件</h1>
    <pre id="output">等待設備方向數據...</pre>
</body>
</html>
```

## 解釋
在使用 `DeviceOrientationEvent` 時，開發者可能會遇到以下常見問題：
- **權限問題**：某些瀏覽器要求使用者授予權限才能訪問設備的方向數據。請確保在 HTTPS 環境中使用。
- **設備兼容性**：並非所有設備都支持該 API，因此在實作時需要進行檢查。
- **數據精度**：設備的傳感器可能會受到環境因素的影響，導致數據不穩定。

## 一句總結
`DeviceOrientationEvent` 是一個強大的 JavaScript API，允許開發者獲取設備的方向和運動數據，以增強網頁的互動性和使用體驗。