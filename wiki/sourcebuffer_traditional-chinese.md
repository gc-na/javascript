<!--
Meta Description: # SourceBuffer 在 JavaScript 中的應用與使用指南 ## 摘要 SourceBuffer 是一個在 JavaScript 中用於處理媒體流的接口，特別是在使用 MediaSource API 時，用於動態地向媒體緩衝區添加資料。 ## 文檔 ### 目的 SourceBuff...
Meta Keywords: sourcebuffer, mediasource, video, javascript, addsourcebuffer
-->

# SourceBuffer 在 JavaScript 中的應用與使用指南

## 摘要
SourceBuffer 是一個在 JavaScript 中用於處理媒體流的接口，特別是在使用 MediaSource API 時，用於動態地向媒體緩衝區添加資料。

## 文檔
### 目的
SourceBuffer 主要用於管理媒體資料的緩衝，特別是在播放音頻或視頻時。它提供了一個接口來添加、移除和修改媒體數據，並確保流暢的播放體驗。

### 使用
要使用 SourceBuffer，首先需要創建一個 MediaSource 對象，然後將其附加到 HTML 的 `<video>` 或 `<audio>` 元素上。接著，通過 MediaSource 的 `addSourceBuffer` 方法創建 SourceBuffer 實例。

### 詳細信息
- **建立**: 使用 `MediaSource.addSourceBuffer(mimeType)` 方法來建立一個新的 SourceBuffer。
- **添加資料**: 使用 `appendBuffer(data)` 方法將資料添加到 SourceBuffer 中。
- **移除資料**: 使用 `remove(start, end)` 方法從 SourceBuffer 中移除指定範圍的資料。
- **事件處理**: SourceBuffer 支持多種事件，比如 `updateend` 和 `error`，可以用來監控狀態變化。

## 範例
### 基本使用範例
```javascript
// 創建 MediaSource 對象
const mediaSource = new MediaSource();
const video = document.querySelector('video');
video.src = URL.createObjectURL(mediaSource);

// 當 MediaSource 可用時
mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');

    // 添加媒體資料
    fetch('media.mp4')
        .then(response => response.arrayBuffer())
        .then(data => {
            sourceBuffer.appendBuffer(data);
        });
});
```

## 解釋
### 常見陷阱
- **資料格式問題**: 確保添加的資料與 SourceBuffer 的 mimeType 相符，否則會造成錯誤。
- **更新狀態**: 在進行資料的添加或移除時，需注意 SourceBuffer 的狀態，避免在更新進行中再次進行操作。

### 附加說明
- SourceBuffer 只能在 MediaSource 的 `sourceopen` 事件後使用。
- 確保在資料添加完成後處理後續的播放邏輯。

## 單行摘要
SourceBuffer 是一個 JavaScript 接口，用於動態管理媒體流的緩衝區，以實現流暢的音視頻播放體驗。