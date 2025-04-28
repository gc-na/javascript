<!--
Meta Description: # JavaScript 地理定位 (Geolocation) 功能詳解 ## 簡介 JavaScript 的地理定位功能允許網頁訪問用戶的地理位置，這對於提供個性化的服務和增強用戶體驗至關重要。透過 `Geolocation` API，開發者可以獲取用戶的緯度和經度資訊。 ## 文件說明 ### ...
Meta Keywords: geolocation, console, navigator, position, log
-->

# JavaScript 地理定位 (Geolocation) 功能詳解

## 簡介
JavaScript 的地理定位功能允許網頁訪問用戶的地理位置，這對於提供個性化的服務和增強用戶體驗至關重要。透過 `Geolocation` API，開發者可以獲取用戶的緯度和經度資訊。

## 文件說明
### 目的
`Geolocation` API 的主要目的是提供一種方便的方式來取得用戶的地理位置信息。這對於地圖應用、附近商家查詢以及社交媒體功能等場景特別有用。

### 用法
要使用地理定位功能，開發者需要調用 `navigator.geolocation` 物件的方法。最常用的方法包括：
- `getCurrentPosition()`: 獲取用戶當前的地理位置。
- `watchPosition()`: 持續監控用戶的位置變化。
- `clearWatch()`: 停止監控用戶的位置。

### 詳細資訊
- **使用權限**: 瀏覽器會要求用戶授權才能訪問其位置資訊。未獲得授權將無法獲取位置信息。
- **回調函數**: `getCurrentPosition()` 和 `watchPosition()` 方法都需要提供成功和失敗的回調函數，以處理位置信息或錯誤情況。
- **精確度**: 獲取位置的精確度依賴於用戶設備和網絡狀態，位置可能會有誤差。

## 範例
### 獲取當前位置
```javascript
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(
    (position) => {
      console.log('緯度: ' + position.coords.latitude);
      console.log('經度: ' + position.coords.longitude);
    },
    (error) => {
      console.error('錯誤碼: ' + error.code);
    }
  );
} else {
  console.log('抱歉，您的瀏覽器不支援地理定位。');
}
```

### 監控位置變化
```javascript
if (navigator.geolocation) {
  const watchId = navigator.geolocation.watchPosition(
    (position) => {
      console.log('新緯度: ' + position.coords.latitude);
      console.log('新經度: ' + position.coords.longitude);
    },
    (error) => {
      console.error('錯誤碼: ' + error.code);
    }
  );

  // 停止監控
  // navigator.geolocation.clearWatch(watchId);
} else {
  console.log('抱歉，您的瀏覽器不支援地理定位。');
}
```

## 解釋
- **權限問題**: 用戶必須授權才能使用地理定位功能。如果用戶拒絕授權，將無法獲取位置。
- **網路影響**: 在某些情況下，例如使用 Wi-Fi 或 GPS 設備，位置獲取的速度和準確性會有所不同。
- **隱私考量**: 開發者應確保在使用地理定位時遵守隱私政策，並告知用戶其數據的使用方式。

## 總結
JavaScript 的地理定位功能是一個強大的工具，能夠幫助開發者獲取用戶的實時位置資訊，從而提供更為個性化的用戶體驗。