<!--
Meta Description: # 重力感測器 (GravitySensor) 在 JavaScript 中的應用 ## 簡介 重力感測器 (GravitySensor) 是一種 Web API，使開發者能夠訪問設備的重力感測數據，從而進行基於重力的操作和互動。這對於開發遊戲、增強現實 (AR) 應用或任何需要感知設備方向的應用尤...
Meta Keywords: gravitysensor, sensor, 重力感測器, console, api
-->

# 重力感測器 (GravitySensor) 在 JavaScript 中的應用

## 簡介
重力感測器 (GravitySensor) 是一種 Web API，使開發者能夠訪問設備的重力感測數據，從而進行基於重力的操作和互動。這對於開發遊戲、增強現實 (AR) 應用或任何需要感知設備方向的應用尤為重要。

## 文件說明
重力感測器 API 提供了一種方式來獲取設備在三個維度上 (X、Y、Z) 的重力加速度。這些數據可以用來創建動態效果，或根據設備的傾斜角度調整應用的行為。

### 用法
要使用重力感測器，您需要創建一個 `GravitySensor` 的實例，然後訂閱其數據更新。以下是基本的使用步驟：

1. **檢查支持性**：在使用之前，確認瀏覽器是否支持重力感測器。
2. **創建實例**：使用 `new GravitySensor()` 創建實例。
3. **添加事件監聽器**：監聽 `reading` 事件來獲取數據。
4. **啟動感測器**：呼叫 `start()` 方法開始接收數據。

### 代碼範例
```javascript
if ('GravitySensor' in window) {
    const sensor = new GravitySensor();

    sensor.addEventListener('reading', () => {
        console.log(`重力加速度 X: ${sensor.x}`);
        console.log(`重力加速度 Y: ${sensor.y}`);
        console.log(`重力加速度 Z: ${sensor.z}`);
    });

    sensor.start();
} else {
    console.error('此瀏覽器不支持重力感測器');
}
```

## 解釋
在使用重力感測器時，開發者需要注意以下幾點：

- **瀏覽器支持**：並非所有瀏覽器都支持重力感測器，開發者應該在使用之前檢查兼容性。
- **權限問題**：某些瀏覽器可能要求用戶授予權限才能使用感測器功能。
- **數據處理**：重力數據是相對的，開發者需要根據應用需求進行適當的數據處理和轉換。

## 總結
重力感測器 API 提供了一種簡便的方法來獲取設備的重力數據，使開發者能夠創建更互動、動態的應用。