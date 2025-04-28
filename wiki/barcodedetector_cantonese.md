<!--
Meta Description: # BarcodeDetector：JavaScript 中的條碼檢測器 ## 概述 BarcodeDetector 是一個 JavaScript API，允許開發者在網頁上檢測和解析條碼與 QR 碼。這個功能可以用於各種應用，包括電子商務、庫存管理及用戶身份驗證等。 ## 文件說明 ### 目的 ...
Meta Keywords: barcodedetector, javascript, const, detect, imagebitmap
-->

# BarcodeDetector：JavaScript 中的條碼檢測器

## 概述
BarcodeDetector 是一個 JavaScript API，允許開發者在網頁上檢測和解析條碼與 QR 碼。這個功能可以用於各種應用，包括電子商務、庫存管理及用戶身份驗證等。

## 文件說明
### 目的
BarcodeDetector 提供了一個簡單的方法來識別圖像中的條碼。它支持多種條碼格式，包括 QR 碼、EAN、UPC 等，並能夠在相機或靜態圖像中進行檢測。

### 使用方法
要使用 BarcodeDetector，你需要在支持的瀏覽器環境中創建一個條碼檢測器的實例，並調用其 `detect` 方法。以下是基本的語法結構：

```javascript
const barcodeDetector = new BarcodeDetector({ formats: ['qr_code', 'ean_13'] });
```

然後，可以使用 `detect` 方法來檢測圖像中的條碼：

```javascript
barcodeDetector.detect(imageBitmap)
  .then(barcodes => {
    console.log(barcodes);
  })
  .catch(err => {
    console.error(err);
  });
```

### 參數說明
- `formats`: 一個字符串數組，指定要檢測的條碼類型。
- `imageBitmap`: 要檢測的圖像，可以是來自 `<canvas>` 或 `<video>` 的圖像位圖。

## 範例
### 基本使用範例
```javascript
// 創建 BarcodeDetector 實例
const barcodeDetector = new BarcodeDetector({ formats: ['qr_code'] });

// 獲取圖像位圖（例如從 canvas）
const canvas = document.getElementById('myCanvas');
const imageBitmap = canvas.transferToImageBitmap();

// 檢測條碼
barcodeDetector.detect(imageBitmap)
  .then(barcodes => {
    barcodes.forEach(barcode => {
      console.log(`條碼內容: ${barcode.rawValue}`);
      console.log(`條碼類型: ${barcode.format}`);
    });
  })
  .catch(err => {
    console.error('檢測錯誤:', err);
  });
```

### 從視頻中檢測條碼
```javascript
const video = document.getElementById('videoElement');
video.addEventListener('loadeddata', () => {
  const barcodeDetector = new BarcodeDetector({ formats: ['qr_code'] });
  
  setInterval(() => {
    const imageBitmap = video.captureStream().getVideoTracks()[0];
    barcodeDetector.detect(imageBitmap)
      .then(barcodes => {
        // 處理檢測到的條碼
      })
      .catch(err => {
        console.error('檢測錯誤:', err);
      });
  }, 1000);
});
```

## 解釋
### 常見陷阱與注意事項
1. **瀏覽器支持**：BarcodeDetector 目前僅在某些瀏覽器（如 Chrome 和 Edge）中受支持，因此在其他瀏覽器中使用時需要檢查支持情況。
2. **圖像質量**：條碼檢測的準確性取決於圖像的質量。模糊或低解析度的圖像可能導致檢測失敗。
3. **格式選擇**：確保在創建 BarcodeDetector 實例時選擇正確的條碼格式，否則可能無法檢測到條碼。
4. **異步操作**：`detect` 方法返回一個 Promise，因此需要妥善處理異步操作，確保在檢測完成後再進行後續處理。

## 總結
BarcodeDetector 是一個強大的工具，幫助開發者在 JavaScript 中輕鬆實現條碼檢測功能。