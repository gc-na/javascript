<!--
Meta Description: # JavaScript 地理定位 (Geolocation) 功能詳解 ## 簡介 JavaScript 的地理定位功能允許網站或應用程式獲取使用者的地理位置資訊，這對於提供個性化服務和增強用戶體驗至關重要。 ## 文檔 ### 目的 地理定位 API 使開發者能夠訪問設備的位置信息，包括經度和緯...
Meta Keywords: console, geolocation, position, error, javascript
-->

# JavaScript 地理定位 (Geolocation) 功能詳解

## 簡介
JavaScript 的地理定位功能允許網站或應用程式獲取使用者的地理位置資訊，這對於提供個性化服務和增強用戶體驗至關重要。

## 文檔
### 目的
地理定位 API 使開發者能夠訪問設備的位置信息，包括經度和緯度，從而實現地理相關的功能，如地圖顯示、附近商家查詢等。

### 使用方法
要使用地理定位 API，需調用 `navigator.geolocation` 物件的相應方法。主要的方法包括：

- `getCurrentPosition(successCallback, errorCallback, options)`
- `watchPosition(successCallback, errorCallback, options)`
- `clearWatch(watchId)`

**參數說明：**
- `successCallback`：成功獲取位置時的回調函數。
- `errorCallback`：獲取位置失敗時的回調函數。
- `options`：可選的配置對象，包括 `enableHighAccuracy`、`timeout` 和 `maximumAge`。

### 詳細步驟
1. 確保使用 HTTPS 協議，因為地理定位 API 在非安全環境下無法使用。
2. 調用 `getCurrentPosition` 或 `watchPosition` 方法來獲取位置。
3. 處理成功和錯誤回調，並在成功時使用返回的位置信息。

## 範例
### 獲取當前位置
```javascript
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(
    function(position) {
      console.log("經度: " + position.coords.longitude);
      console.log("緯度: " + position.coords.latitude);
    },
    function(error) {
      console.error("獲取位置失敗: " + error.message);
    }
  );
} else {
  console.log("此瀏覽器不支持地理定位。");
}
```

### 持續追蹤位置
```javascript
let watchId = navigator.geolocation.watchPosition(
  function(position) {
    console.log("當前經度: " + position.coords.longitude);
    console.log("當前緯度: " + position.coords.latitude);
  },
  function(error) {
    console.error("獲取位置失敗: " + error.message);
  }
);

// 停止追蹤位置
navigator.geolocation.clearWatch(watchId);
```

## 解釋
### 常見問題
- **權限問題**：使用者必須允許網站或應用程式獲取其位置資訊。若拒絕，將不會獲得位置信息。
- **準確性**：`enableHighAccuracy` 選項可以提高定位準確性，但會增加電池消耗。
- **跨域問題**：在某些環境下，可能會遇到跨域限制，需確保正確的 HTTP 標頭配置。

## 一句總結
JavaScript 的地理定位 API 使開發者能夠輕鬆獲取並使用使用者的地理位置信息，增強應用的互動性和實用性。