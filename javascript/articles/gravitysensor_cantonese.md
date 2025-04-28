<!--
Meta Description: # GravitySensor：JavaScript 中的重力感應器 ## 簡介 GravitySensor 是一種用於獲取設備重力數據的 Web API，允許開發者在網頁應用中使用重力感應功能。這對於創建互動式遊戲或應用程序非常有用。 ## 文檔 ### 目的 GravitySensor API ...
Meta Keywords: gravitysensor, sensor, javascript, reading, console
-->

# GravitySensor：JavaScript 中的重力感應器

## 簡介
GravitySensor 是一種用於獲取設備重力數據的 Web API，允許開發者在網頁應用中使用重力感應功能。這對於創建互動式遊戲或應用程序非常有用。

## 文檔
### 目的
GravitySensor API 旨在提供設備在三維空間中的重力向量數據，幫助開發者獲取設備的傾斜和運動信息。

### 使用方法
要使用 GravitySensor，開發者需先創建一個 GravitySensor 的實例並添加事件監聽器來獲取重力數據。以下是基本的使用步驟：

1. 檢查瀏覽器是否支持 GravitySensor。
2. 創建 GravitySensor 實例。
3. 添加 `reading` 事件的監聽器。
4. 啟動感應器。

### 詳細信息
```javascript
if ('GravitySensor' in window) {
    const sensor = new GravitySensor();

    sensor.addEventListener('reading', () => {
        console.log(`重力數據：x=${sensor.x}, y=${sensor.y}, z=${sensor.z}`);
    });

    sensor.start();
} else {
    console.error('此瀏覽器不支持 GravitySensor');
}
```
在這段代碼中，`GravitySensor` 會持續更新 x、y 和 z 軸的重力數據，並在每次讀取時觸發 `reading` 事件。

## 示例
### 基本用法
```javascript
if ('GravitySensor' in window) {
    const sensor = new GravitySensor();
    
    sensor.addEventListener('reading', () => {
        console.log(`重力數據：x=${sensor.x.toFixed(2)}, y=${sensor.y.toFixed(2)}, z=${sensor.z.toFixed(2)}`);
    });

    sensor.start();
} else {
    console.log("重力感應器不受支持。");
}
```

### 停止感應器
```javascript
sensor.stop();
```
在需要停止重力感應器時，可以調用 `stop` 方法。

## 解釋
### 常見陷阱
- **瀏覽器兼容性**：並非所有瀏覽器都支持 GravitySensor，開發者應該在使用前進行檢查。
- **權限問題**：某些瀏覽器可能要求用戶授予權限才能使用感應器功能。
- **性能影響**：持續讀取感應器數據可能會影響應用性能，建議只在需要的時候啟動感應器。

### 注意事項
- 確保在頁面加載完成後再實例化感應器。
- 使用 `toFixed()` 方法來控制輸出的數字精度。

## 一句話總結
GravitySensor 是一個強大的工具，使開發者能夠在 JavaScript 應用中獲取設備的重力數據，增強用戶互動體驗。