<!--
Meta Description: # JavaScript 條碼檢測器 (BarcodeDetector) ## 簡介 JavaScript 條碼檢測器 (BarcodeDetector) 是一個用於在網頁中識別和解讀條碼的 API。利用這個功能，開發者可以輕鬆地在用戶設備上進行條碼掃描，增強應用程式的互動性和功能性。 ## 文檔 ...
Meta Keywords: barcodedetector, const, canvas, javascript, api
-->

# JavaScript 條碼檢測器 (BarcodeDetector)

## 簡介
JavaScript 條碼檢測器 (BarcodeDetector) 是一個用於在網頁中識別和解讀條碼的 API。利用這個功能，開發者可以輕鬆地在用戶設備上進行條碼掃描，增強應用程式的互動性和功能性。

## 文檔
### 目的
條碼檢測器 API 使得開發者能夠利用設備的相機來自動識別條碼。這對於電子商務、庫存管理和其他需要條碼掃描的應用非常有用。

### 使用方式
要使用條碼檢測器，首先需要檢查瀏覽器是否支援該 API。然後，可以創建一個 `BarcodeDetector` 實例，並使用其 `detect` 方法來分析視頻流中的條碼。

#### 基本語法
```javascript
const barcodeDetector = new BarcodeDetector({ formats: ['ean_13', 'qr_code'] });
```

### 參數
- `formats`: 一個字符串數組，指定要識別的條碼格式，如 `'ean_13'`、`'qr_code'` 等。

### 方法
- `detect(videoFrame)`: 
  - **參數**: `videoFrame` - 一個影像數據或視頻幀。
  - **返回**: 返回一個包含識別到的條碼信息的 Promise。

## 範例
```javascript
// 檢查瀏覽器是否支援條碼檢測器
if ('BarcodeDetector' in window) {
  const barcodeDetector = new BarcodeDetector({ formats: ['ean_13', 'qr_code'] });

  // 取得視頻流
  const video = document.querySelector('video');
  const canvas = document.createElement('canvas');
  const context = canvas.getContext('2d');

  // 在視頻流中識別條碼
  video.addEventListener('play', async () => {
    while (true) {
      context.drawImage(video, 0, 0, canvas.width, canvas.height);
      const barcodeData = await barcodeDetector.detect(canvas);
      console.log(barcodeData);
      await new Promise(resolve => setTimeout(resolve, 1000)); // 每秒檢測一次
    }
  });
}
```

## 說明
在使用 `BarcodeDetector` 時，有幾個常見的陷阱需要注意：
- 瀏覽器兼容性：並非所有瀏覽器都支持條碼檢測器 API，特別是較舊的版本。請確認用戶的瀏覽器版本。
- 硬件限制：某些設備的相機可能無法提供足夠的解析度來正確識別條碼。
- 環境影響：光線不足或條碼模糊會影響檢測的準確性。

## 總結
JavaScript 條碼檢測器 API 提供了一個方便的方式來識別和解析條碼，使開發者能夠創建更具互動性的應用程序。