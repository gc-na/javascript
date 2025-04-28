<!--
Meta Description: # MediaCapabilities：JavaScript 中的媒體能力檢查 ## 概述 `MediaCapabilities` 是一個 JavaScript API，允許開發者檢查瀏覽器支持的媒體編碼、解碼能力以及播放性能，以便優化媒體內容的使用。 ## 文檔 ### 目的 `MediaCapa...
Meta Keywords: mediacapabilities, decodinginfo, promise, mediatype, contenttype
-->

# MediaCapabilities：JavaScript 中的媒體能力檢查

## 概述
`MediaCapabilities` 是一個 JavaScript API，允許開發者檢查瀏覽器支持的媒體編碼、解碼能力以及播放性能，以便優化媒體內容的使用。

## 文檔
### 目的
`MediaCapabilities` 的主要目的是讓開發者能夠獲取有關媒體格式的支持程度，包括影片和音訊的解碼能力。這對於確保媒體內容在不同設備和瀏覽器上流暢播放至關重要。

### 使用方法
要使用 `MediaCapabilities` API，開發者可以調用 `MediaCapabilities.decodingInfo()` 方法，該方法返回一個 Promise，表示特定媒體格式的支持情況。

### 詳細信息
`MediaCapabilities` 提供了以下屬性和方法：

- `decodingInfo(mediaType, contentType, hardwareAcceleration)`：
  - **參數**：
    - `mediaType`: 媒體類型（例如：'file'或'stream'）
    - `contentType`: 媒體格式（例如：'video/mp4'）
    - `hardwareAcceleration`: 是否使用硬件加速（`true` 或 `false`）
  - **返回**：返回一個 Promise，解析為包含支持信息的對象。

### 支持信息對象示例
返回的對象包含以下屬性：
- `supported`: 布林值，表示是否支持該媒體格式。
- `smooth`: 布林值，表示在支持的情況下播放是否流暢。
- `powerEfficient`: 布林值，表示播放是否為節能模式。

## 例子
以下是使用 `MediaCapabilities` 的基本示例：

```javascript
async function checkMediaCapabilities() {
    const mediaType = 'file';
    const contentType = 'video/mp4';
    const hardwareAcceleration = true;

    try {
        const capabilities = await navigator.mediaCapabilities.decodingInfo(mediaType, contentType, hardwareAcceleration);
        console.log(capabilities);
    } catch (error) {
        console.error('無法檢查媒體能力:', error);
    }
}

checkMediaCapabilities();
```

此示例檢查瀏覽器是否支持 MP4 格式的視頻播放，並打印出支持信息。

## 解釋
### 常見陷阱
- **不支持的格式**：有些瀏覽器可能不支持某些媒體格式，這可能會導致 `decodingInfo` 返回的 `supported` 屬性為 `false`。
- **硬件加速的限制**：即使某個格式被支持，硬件加速可能也不一定可用，這要依賴於用戶的設備和瀏覽器設置。
- **Promise 的處理**：確保使用 `async/await` 或 `.then()` 方法正確處理 Promise，否則可能導致錯誤未被捕獲。

## 總結
`MediaCapabilities` API 提供了一個有效的方法來檢查瀏覽器支持的媒體格式，幫助開發者優化媒體內容的播放性能。