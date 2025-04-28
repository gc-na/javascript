<!--
Meta Description: # DevicePosture：JavaScript 中的設備姿態檢測 ## 概述 DevicePosture 是一項新興的 Web API，旨在允許開發者檢測裝置的姿態，例如設備是否垂直或水平放置。這對於提升用戶體驗尤為重要，尤其在需要根據設備姿態調整內容顯示或交互方式的應用程序中。 ## 文檔 ...
Meta Keywords: deviceposture, api, navigator, orientation, javascript
-->

# DevicePosture：JavaScript 中的設備姿態檢測

## 概述
DevicePosture 是一項新興的 Web API，旨在允許開發者檢測裝置的姿態，例如設備是否垂直或水平放置。這對於提升用戶體驗尤為重要，尤其在需要根據設備姿態調整內容顯示或交互方式的應用程序中。

## 文檔

### 目的
DevicePosture API 使網頁能夠獲取設備的姿態信息，提供用於響應式設計和優化用戶體驗的功能。隨著移動設備的普及，這項功能可以幫助開發者更好地適應各種屏幕方向和使用場景。

### 使用方式
要使用 DevicePosture API，您需要確保您的環境支持該 API。一般來說，這可以通過以下步驟來實現：

1. 確認瀏覽器支持 DevicePosture API。
2. 使用 `navigator.devicePosture` 來訪問設備姿態信息。

以下是獲取設備姿態的基本語法：

```javascript
if ('DevicePosture' in navigator) {
    // 設備姿態 API 可用
    const posture = navigator.devicePosture;
    console.log(posture);
} else {
    console.log('該瀏覽器不支持 DevicePosture API');
}
```

### 詳情
DevicePosture API 提供了以下幾個重要屬性和方法：

- `navigator.devicePosture`：此屬性返回一個包含設備姿態信息的對象。
- `devicePosture.orientation`：返回設備的當前方向（例如，"landscape" 或 "portrait"）。
- `devicePosture.onchange`：當設備姿態發生改變時觸發的事件。

這些屬性和方法使得開發者能夠輕鬆獲取和監聽設備姿態的變化。

## 範例

### 基本使用範例
以下是如何使用 DevicePosture API 來檢測並顯示設備姿態的簡單範例：

```javascript
if ('DevicePosture' in navigator) {
    navigator.devicePosture.onchange = function() {
        const orientation = navigator.devicePosture.orientation;
        alert(`當前設備姿態是：${orientation}`);
    };
} else {
    console.log('該瀏覽器不支持 DevicePosture API');
}
```

在這個範例中，當設備姿態改變時，會顯示一個提示框，告訴用戶當前的設備姿態。

## 解釋

### 常見陷阱
1. **瀏覽器支持性**：並非所有瀏覽器都支持 DevicePosture API，因此在使用前應進行支持性檢查。
2. **事件監聽**：如果未正確設置 `onchange` 事件，可能無法獲取姿態變化的通知。
3. **隱私問題**：獲取設備姿態可能會引起某些用戶對隱私的擔憂，開發者應在使用時明確告知用戶。

## 總結
DevicePosture API 允許開發者檢測設備的姿態，從而根據用戶的設備方向調整顯示內容和交互方式，提升用戶體驗。