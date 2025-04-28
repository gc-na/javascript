<!--
Meta Description: # ondevicemotion 事件 - JavaScript 的全面指南 ## 概述 `ondevicemotion` 是一個用於監聽設備運動的事件，常用於移動設備的 JavaScript 應用程式中，讓開發者能夠獲取設備的加速度和旋轉速率等資訊。 ## 文檔 ### 目的 `ondevicem...
Meta Keywords: ondevicemotion, javascript, devicemotion, event, acceleration
-->

# ondevicemotion 事件 - JavaScript 的全面指南

## 概述
`ondevicemotion` 是一個用於監聽設備運動的事件，常用於移動設備的 JavaScript 應用程式中，讓開發者能夠獲取設備的加速度和旋轉速率等資訊。

## 文檔
### 目的
`ondevicemotion` 事件允許開發者獲取設備的加速度和旋轉資訊，這對於創建互動式應用程式和遊戲至關重要。此事件提供了在三個坐標軸上的加速度數據，幫助開發者實現基於設備運動的功能。

### 用法
要使用 `ondevicemotion` 事件，開發者需為 `window` 物件添加一個事件監聽器，並在事件觸發時執行相應的回調函數。

#### 語法
```javascript
window.addEventListener('devicemotion', function(event) {
    // 事件處理程式
});
```

### 詳細信息
`devicemotion` 事件提供以下屬性：

- `acceleration`：一個包含 x、y 和 z 軸加速度的物件。
- `accelerationIncludingGravity`：一個包含重力影響的加速度物件。
- `rotationRate`：一個包含 x、y 和 z 軸旋轉速率的物件。
- `interval`：事件的時間間隔，通常以毫秒為單位。

## 範例
以下是使用 `ondevicemotion` 的基本範例：

```javascript
window.addEventListener('devicemotion', function(event) {
    const acceleration = event.acceleration;
    const rotationRate = event.rotationRate;

    console.log('加速度:', acceleration);
    console.log('旋轉速率:', rotationRate);
});
```

## 解釋
使用 `ondevicemotion` 時，開發者需注意以下幾點：

- **權限問題**：某些瀏覽器要求用戶授權才能訪問設備運動數據。確保在應用中適當處理這些權限請求。
- **性能影響**：頻繁的事件觸發可能導致性能問題，建議在應用中進行適當的節流或防抖處理。
- **設備支持**：並非所有設備都支持 `devicemotion` 事件，需進行兼容性檢查。

## 總結
`ondevicemotion` 事件是一個強大的工具，能夠讓開發者創造出基於設備運動的互動性應用。