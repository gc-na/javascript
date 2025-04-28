<!--
Meta Description: # MediaDevices：JavaScript 中的媒體設備訪問 ## 概要 MediaDevices 是一個 Web API，允許開發者訪問用戶的媒體設備，例如相機和麥克風，從而實現音視頻通話、錄音和拍照等功能。 ## 文檔 ### 目的 MediaDevices API 提供了訪問用戶設備的...
Meta Keywords: mediadevices, api, getusermedia, videoelement, javascript
-->

# MediaDevices：JavaScript 中的媒體設備訪問

## 概要
MediaDevices 是一個 Web API，允許開發者訪問用戶的媒體設備，例如相機和麥克風，從而實現音視頻通話、錄音和拍照等功能。

## 文檔
### 目的
MediaDevices API 提供了訪問用戶設備的功能，這對於需要音視頻交互的應用程序尤為重要。它可以讓開發者獲取可用的媒體輸入源，並進行流媒體處理。

### 用法
要使用 MediaDevices API，開發者需要首先確認用戶的權限，然後可以使用 `getUserMedia()` 方法請求音視頻流。該方法返回一個 Promise，當用戶授予權限時，Promise 會解析為 `MediaStream` 對象。

### 詳細說明
- **獲取媒體流**：使用 `navigator.mediaDevices.getUserMedia(constraints)` 方法來獲取音視頻流。
- **約束條件**：`constraints` 參數可以指定音視頻的配置需求，如音頻的是否開啟、視頻的解析度等。
- **權限請求**：用戶的瀏覽器會提示用戶授予或拒絕訪問設備的權限。

## 範例
以下是使用 MediaDevices API 獲取視頻流的基本範例：

```javascript
navigator.mediaDevices.getUserMedia({ video: true })
    .then(function(stream) {
        const videoElement = document.querySelector('video');
        videoElement.srcObject = stream;
        videoElement.play();
    })
    .catch(function(err) {
        console.error("獲取媒體流失敗:", err);
    });
```

## 解釋
- **常見陷阱**：確保在 HTTPS 協議下運行，因為某些瀏覽器不允許在非安全環境下訪問媒體設備。
- **用戶授權**：用戶可能會拒絕訪問權限，開發者應該考慮到這種情況並提供適當的錯誤處理。
- **瀏覽器兼容性**：不同瀏覽器對 MediaDevices API 的支持程度不同，因此在實施時應檢查兼容性。

## 一句總結
MediaDevices API 是一個強大的工具，讓開發者可以輕鬆訪問用戶的媒體設備並實現音視頻功能。