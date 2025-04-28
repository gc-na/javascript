<!--
Meta Description: # MediaSource 在 JavaScript 中的應用 ## 簡介 MediaSource 是一個 JavaScript API，允許開發者動態地控制媒體流的播放，特別是針對視頻和音頻的串流。它使得在網頁應用中實現自適應串流成為可能。 ## 文檔 ### 目的 MediaSource 主要用...
Meta Keywords: mediasource, sourcebuffer, video, javascript, const
-->

# MediaSource 在 JavaScript 中的應用

## 簡介
MediaSource 是一個 JavaScript API，允許開發者動態地控制媒體流的播放，特別是針對視頻和音頻的串流。它使得在網頁應用中實現自適應串流成為可能。

## 文檔
### 目的
MediaSource 主要用於在網頁中動態地管理多媒體內容。透過這個 API，開發者可以在媒體播放過程中添加、移除或更新媒體片段，以實現更流暢的用戶體驗。

### 用法
要使用 MediaSource，首先需要創建一個 MediaSource 實例，然後將其附加到 HTML 的 `<video>` 或 `<audio>` 標籤。接下來，開發者可以使用 `SourceBuffer` 來添加媒體數據。

### 詳細說明
1. **創建 MediaSource**:
   ```javascript
   const mediaSource = new MediaSource();
   const videoElement = document.querySelector('video');
   videoElement.src = URL.createObjectURL(mediaSource);
   ```

2. **添加 SourceBuffer**:
   要添加媒體數據，需創建一個 `SourceBuffer`：
   ```javascript
   mediaSource.addEventListener('sourceopen', function() {
       const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E"');
   });
   ```

3. **添加資料到 SourceBuffer**:
   一旦 `SourceBuffer` 被創建，你可以將媒體數據添加到它：
   ```javascript
   fetch('path/to/video.mp4')
       .then(response => response.arrayBuffer())
       .then(data => {
           sourceBuffer.appendBuffer(data);
       });
   ```

## 範例
以下是一個基本的 MediaSource 使用範例：
```html
<video controls></video>
<script>
   const mediaSource = new MediaSource();
   const videoElement = document.querySelector('video');
   videoElement.src = URL.createObjectURL(mediaSource);

   mediaSource.addEventListener('sourceopen', function() {
       const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E"');

       fetch('path/to/video.mp4')
           .then(response => response.arrayBuffer())
           .then(data => {
               sourceBuffer.appendBuffer(data);
           });
   });
</script>
```

## 解釋
在使用 MediaSource 時，有一些常見的陷阱和注意事項：
- **格式要求**: 確保媒體格式和編碼符合瀏覽器的支持範圍。
- **緩衝管理**: 當 SourceBuffer 中的數據塊過大時，可能會導致錯誤，開發者需妥善管理緩衝區。
- **事件監聽**: 需適當使用事件監聽器來獲取 MediaSource 的狀態變化，以便及時更新媒體播放。

## 總結
MediaSource 是一個強大的 JavaScript API，允許開發者靈活地控制媒體流的播放，為用戶提供流暢且動態的媒體體驗。