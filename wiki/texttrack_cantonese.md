<!--
Meta Description: # JavaScript TextTrack 物件：全面了解及使用指南 ## 概述 TextTrack 物件是 HTML5 視頻和音頻元素中的一個重要組件，主要用於處理媒體的字幕和文本軌道。它允許開發者為多媒體內容添加額外的信息，從而提高可及性和用戶體驗。 ## 文檔 ### 目的 TextTrac...
Meta Keywords: texttrack, track, video, src, javascript
-->

# JavaScript TextTrack 物件：全面了解及使用指南

## 概述
TextTrack 物件是 HTML5 視頻和音頻元素中的一個重要組件，主要用於處理媒體的字幕和文本軌道。它允許開發者為多媒體內容添加額外的信息，從而提高可及性和用戶體驗。

## 文檔
### 目的
TextTrack 物件的主要目的是提供對媒體文本軌道的控制，例如字幕、標題和描述。這些文本軌道可以幫助聽障人士理解視頻內容，並為多語言觀眾提供便利。

### 使用
TextTrack 物件通常與 `<track>` 標籤一起使用。當使用 `<video>` 或 `<audio>` 元素時，開發者可以通過 `<track>` 標籤來添加字幕或其他文本軌道。TextTrack 物件包括多個屬性和方法，可以用來操控文本的顯示和行為。

### 主要屬性
- **id**: 唯一標識符，便於識別不同的文本軌道。
- **kind**: 指定文本軌道的類型（例如：subtitles、captions、descriptions）。
- **label**: 用於顯示的文本標籤，通常是用於描述該文本軌道的語言或內容。
- **language**: 指定文本的語言。
- **mode**: 控制文本的顯示模式（例如：hidden、showing）。

### 主要方法
- **addCue(cue)**: 添加一個新的字幕線索。
- **removeCue(cue)**: 移除已存在的字幕線索。

## 範例
以下是如何使用 TextTrack 物件的基本範例：

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
  <track kind="subtitles" src="subtitles_cantonese.vtt" srclang="zh-HK" label="Cantonese">
  Your browser does not support the video tag.
</video>
```

在 JavaScript 中操作 TextTrack：

```javascript
const video = document.querySelector('video');
const track = video.textTracks[0]; // 獲取第一個文本軌道

track.mode = 'showing'; // 顯示字幕
track.addCue(new VTTCue(0, 10, '這是字幕範例')); // 添加字幕線索
```

## 解釋
在使用 TextTrack 時，有幾個常見的陷阱和注意事項：
- 確保 `<track>` 標籤的 `src` 屬性指向正確的 WebVTT 文件，否則字幕將不會顯示。
- `mode` 屬性可以影響字幕的顯示，因此在操作之前需確保其設置正確。
- 不同的瀏覽器對 TextTrack 的支持程度可能有所不同，建議在多個平台上測試效果。

## 一句總結
TextTrack 物件是用於為 HTML5 媒體元素添加和控制字幕的強大工具。