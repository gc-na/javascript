<!--
Meta Description: # SourceBuffer：JavaScript 中的媒體數據緩衝區 ## 摘要 `SourceBuffer` 是一個 Web API 的組件，主要用於媒體串流的控制和管理。它允許開發者在媒體播放過程中動態添加和修改媒體數據。 ## 文件說明 `SourceBuffer` 是 `MediaSour...
Meta Keywords: sourcebuffer, mediasource, javascript, video, const
-->

# SourceBuffer：JavaScript 中的媒體數據緩衝區

## 摘要
`SourceBuffer` 是一個 Web API 的組件，主要用於媒體串流的控制和管理。它允許開發者在媒體播放過程中動態添加和修改媒體數據。

## 文件說明
`SourceBuffer` 是 `MediaSource` 介面的實例，設計用來支持媒體流的編碼和解碼。開發者可以利用 `SourceBuffer` 來向媒體源添加多段數據，從而實現串流播放功能。這使得在網頁上播放音頻和視頻變得更加靈活和高效。

### 目的
`SourceBuffer` 的主要目的是讓開發者能夠隨時向媒體播放中添加新的數據，而不需要重新載入整個媒體資源。這一功能特別適合用於直播、點播及動態內容的播放。

### 使用
要使用 `SourceBuffer`，首先需要創建一個 `MediaSource` 實例，然後調用 `.addSourceBuffer()` 方法來創建新的 `SourceBuffer`。接下來，可以使用 `.appendBuffer()` 方法向 `SourceBuffer` 添加媒體數據。

### 詳細信息
- **創建 `MediaSource`：**
  ```javascript
  const mediaSource = new MediaSource();
  ```

- **添加 `SourceBuffer`：**
  ```javascript
  const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
  ```

- **添加數據到 `SourceBuffer`：**
  ```javascript
  sourceBuffer.appendBuffer(new Uint8Array(data));
  ```

- **事件監聽：**
  `SourceBuffer` 提供多個事件，例如 `updateend` 和 `error`，用於監控數據添加的狀態。

## 示例
### 基本使用示例
```javascript
const video = document.querySelector('video');
const mediaSource = new MediaSource();

video.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', () => {
  const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
  
  fetch('path/to/video.mp4')
    .then(response => response.arrayBuffer())
    .then(data => {
      sourceBuffer.appendBuffer(data);
    });
});
```

## 解釋
在使用 `SourceBuffer` 時，有幾個常見的陷阱和注意事項：

- **數據格式**：確保添加到 `SourceBuffer` 的數據格式與創建時指定的 MIME 類型相符。
- **更新狀態**：在對 `SourceBuffer` 進行操作時，需注意其更新狀態。操作只能在 `updateend` 事件觸發後進行，否則會導致錯誤。
- **容量限制**：`SourceBuffer` 的大小是有限制的，對於大型媒體文件，可能需要考慮分批添加數據。

## 一句總結
`SourceBuffer` 是一個強大的工具，允許開發者在 JavaScript 中動態管理和控制媒體數據的播放。