<!--
Meta Description: # ImageCapture：JavaScript 中的圖像捕捉功能 ## 摘要 `ImageCapture` 是一個 JavaScript API，旨在從媒體裝置（如相機）捕捉靜態圖像。它提供了一個簡單的界面，用於控制圖像捕捉過程，並支持高效的圖像處理和存儲。 ## 文檔 ### 目的 `Imag...
Meta Keywords: imagecapture, const, javascript, getusermedia, mediastream
-->

# ImageCapture：JavaScript 中的圖像捕捉功能

## 摘要
`ImageCapture` 是一個 JavaScript API，旨在從媒體裝置（如相機）捕捉靜態圖像。它提供了一個簡單的界面，用於控制圖像捕捉過程，並支持高效的圖像處理和存儲。

## 文檔
### 目的
`ImageCapture` 主要用於從媒體流中捕捉單個圖像。這對於需要從網頁應用程序中獲取即時圖像數據的場景（如視頻聊天、拍照應用）非常有用。

### 使用方法
要使用 `ImageCapture`，必須首先獲取一個媒體流，通常是使用 `getUserMedia()` 獲取的。然後，利用 `ImageCapture` 對象進行圖像捕捉。

#### 基本語法
```javascript
const mediaStream = await navigator.mediaDevices.getUserMedia({ video: true });
const videoTrack = mediaStream.getVideoTracks()[0];
const imageCapture = new ImageCapture(videoTrack);
```

### 詳細說明
一旦創建了 `ImageCapture` 對象，就可以使用它的方法來捕捉圖像。常用的方法包括：
- `takePhoto()`：捕捉一張靜態圖像並返回一個 Promise，解析為圖像的 Blob。
- `getPhotoCapabilities()`：獲取相機的拍照能力，如解析度和對焦選項。

## 例子
### 基本用法
下面的範例展示了如何捕捉圖像並顯示在網頁上：

```javascript
async function captureImage() {
    const mediaStream = await navigator.mediaDevices.getUserMedia({ video: true });
    const videoTrack = mediaStream.getVideoTracks()[0];
    const imageCapture = new ImageCapture(videoTrack);

    try {
        const blob = await imageCapture.takePhoto();
        const imgElement = document.createElement('img');
        imgElement.src = URL.createObjectURL(blob);
        document.body.appendChild(imgElement);
    } catch (error) {
        console.error('Error capturing image:', error);
    }
}

captureImage();
```

## 解釋
### 常見問題與注意事項
- **瀏覽器支援**：確保使用的瀏覽器支援 `ImageCapture` API。舊版瀏覽器可能不支持此功能。
- **權限問題**：使用 `getUserMedia()` 時需要用戶授權訪問媒體裝置。
- **流的狀態**：在捕捉圖像前，確保媒體流處於活動狀態，否則可能會導致錯誤。

## 一行總結
`ImageCapture` 是一個強大的 JavaScript API，用於從媒體流捕捉靜態圖像，簡化了圖像處理過程。