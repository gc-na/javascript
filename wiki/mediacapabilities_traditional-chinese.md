<!--
Meta Description: # JavaScript 的 MediaCapabilities API：了解媒體編解碼能力 ## 概要 MediaCapabilities 是一個 JavaScript API，用於檢查用戶設備對於媒體編解碼的支持程度，幫助開發者根據設備特性選擇合適的媒體格式，從而優化媒體播放體驗。 ## 文檔 ...
Meta Keywords: mediacapabilities, api, javascript, promise, type
-->

# JavaScript 的 MediaCapabilities API：了解媒體編解碼能力

## 概要
MediaCapabilities 是一個 JavaScript API，用於檢查用戶設備對於媒體編解碼的支持程度，幫助開發者根據設備特性選擇合適的媒體格式，從而優化媒體播放體驗。

## 文檔
### 目的
MediaCapabilities API 旨在為開發者提供一種方法，以便查詢用戶設備支持的媒體編解碼器的能力，這使得開發者能夠選擇最佳的媒體格式來提高性能和兼容性。

### 使用
要使用 MediaCapabilities API，開發者可以使用 `navigator.mediaCapabilities` 接口來檢查特定媒體格式的支持情況。該 API 主要提供以下方法：

- `navigator.mediaCapabilities.decodingInfo()`: 檢查特定編解碼器的解碼能力。

### 詳細說明
這個 API 主要接受一個包含媒體格式信息的物件作為參數，並返回一個 Promise，該 Promise 解析為一個物件，該物件包含了設備對於該媒體格式的支持情況，包括是否可以穩定解碼、是否支持硬體加速等屬性。

#### 參數範例
```javascript
{
    type: 'media-type', // 媒體類型，例如 'video' 或 'audio'
    contentType: 'mime/type', // 媒體的 MIME 類型，例如 'video/mp4'
    embedded: false, // 媒體是否嵌入在網頁中
    width: 1280, // 媒體的寬度
    height: 720, // 媒體的高度
    bitrate: 500000, // 媒體的比特率
    framerate: 30 // 媒體的幀率
}
```

## 示例
以下是一個簡單的示例，展示如何使用 MediaCapabilities API 檢查設備對於特定視頻編解碼器的支持情況：

```javascript
const mediaConfig = {
    type: 'video',
    contentType: 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"',
    width: 1280,
    height: 720,
    bitrate: 500000,
    framerate: 30
};

navigator.mediaCapabilities.decodingInfo(mediaConfig)
    .then(result => {
        if (result.supported) {
            console.log('設備支持該媒體格式');
        } else {
            console.log('設備不支持該媒體格式');
        }
    })
    .catch(error => {
        console.error('檢查媒體能力時出錯:', error);
    });
```

## 解釋
### 常見問題
- **不支持的媒體格式**：如果開發者請求的媒體格式不被設備支持，`decodingInfo` 方法會返回`{ supported: false }`。這可能會導致媒體無法正確播放。
- **Promise 錯誤處理**：如果在檢查媒體能力時發生錯誤，例如不正確的參數或其他問題，應該妥善處理 Promise 的拒絕情況，以避免應用程式崩潰。

## 一句總結
MediaCapabilities API 使開發者能夠檢查設備對各種媒體格式的支持，從而提升媒體播放的性能和兼容性。