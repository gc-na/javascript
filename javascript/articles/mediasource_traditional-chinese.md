<!--
Meta Description: # MediaSource：JavaScript 中的媒體串流處理 ## 概述 MediaSource 是一個 JavaScript API，允許開發者動態地生成媒體資源，並將其直接附加到 `<video>` 或 `<audio>` 元素上。這個功能特別適合用於需要串流或分段加載的媒體應用。 ## ...
Meta Keywords: mediasource, video, javascript, const, api
-->

# MediaSource：JavaScript 中的媒體串流處理

## 概述
MediaSource 是一個 JavaScript API，允許開發者動態地生成媒體資源，並將其直接附加到 `<video>` 或 `<audio>` 元素上。這個功能特別適合用於需要串流或分段加載的媒體應用。

## 文檔
### 目的
MediaSource API 的主要目的是提供一種靈活的方式來處理媒體數據，允許開發者在播放過程中動態添加或修改媒體內容。這對於實現如直播串流或按需視頻播放等功能非常有用。

### 使用方法
1. **創建 MediaSource 實例**：
   ```javascript
   const mediaSource = new MediaSource();
   ```

2. **將 MediaSource 附加到 `<video>` 元素**：
   ```javascript
   const videoElement = document.getElementById('video');
   videoElement.src = URL.createObjectURL(mediaSource);
   ```

3. **添加來源緩衝區**：
   ```javascript
   const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8"');
   ```

4. **向來源緩衝區添加媒體數據**：
   ```javascript
   fetch('video.webm')
     .then(response => response.arrayBuffer())
     .then(data => {
       sourceBuffer.appendBuffer(data);
     });
   ```

### 詳細說明
- **MediaSource 實例**：每個 MediaSource 實例都可以附加到一個 `<video>` 或 `<audio>` 元素。這允許多個媒體源的動態管理。
- **來源緩衝區**：通過 `addSourceBuffer` 方法添加來源緩衝區，這是一個可管理的媒體數據區域，可以接受媒體數據。
- **事件處理**：MediaSource API 提供了一些事件，如 `sourceopen` 和 `sourceclose`，這些事件可以用來監控媒體來源的狀態。

## 範例
### 基本使用範例
```javascript
const mediaSource = new MediaSource();
const videoElement = document.getElementById('video');
videoElement.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', function () {
   const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8"');
   fetch('video.webm')
     .then(response => response.arrayBuffer())
     .then(data => {
       sourceBuffer.appendBuffer(data);
     });
});
```

## 解釋
### 常見陷阱
- **編碼格式支持**：確保所使用的編碼格式與瀏覽器兼容，否則媒體將無法播放。
- **緩衝區管理**：在向來源緩衝區添加數據之前，必須確保其狀態為可用，否則會出現錯誤。
- **跨域問題**：當從不同域請求媒體文件時，需確保服務器正確設置了 CORS 標頭，以避免請求被阻止。

## 一句總結
MediaSource API 使 JavaScript 開發者能夠動態生成和管理媒體串流，提升用戶的播放體驗。