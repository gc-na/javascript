<!--
Meta Description: # VTTCue: JavaScript 中用於 WebVTT 字幕的物件 ## 概述 VTTCue 是一個 JavaScript 物件，用於表示 WebVTT 字幕中的單個字幕條目，廣泛應用於視頻播放器中，以提供時間控制的字幕顯示。 ## 文件說明 VTTCue 物件是 WebVTT (Web V...
Meta Keywords: vttcue, track, webvtt, cue, javascript
-->

# VTTCue: JavaScript 中用於 WebVTT 字幕的物件

## 概述
VTTCue 是一個 JavaScript 物件，用於表示 WebVTT 字幕中的單個字幕條目，廣泛應用於視頻播放器中，以提供時間控制的字幕顯示。

## 文件說明
VTTCue 物件是 WebVTT (Web Video Text Tracks) 的一部分，主要用於創建和管理視頻中的字幕。它包含開始時間、結束時間、字幕文本和一些其他屬性。VTTCue 使開發者能夠輕鬆地控制字幕的顯示，從而提升用戶的觀看體驗。

### 主要屬性與方法
- **startTime**: 字幕的開始顯示時間（以秒為單位）。
- **endTime**: 字幕的結束顯示時間（以秒為單位）。
- **text**: 顯示的字幕文本。
- **line**: 字幕文本的行位置。
- **position**: 字幕在視窗中的位置（百分比）。
- **align**: 字幕的對齊方式（如左、中、右）。

### 使用方法
VTTCue 物件通常與 HTML5 的 `<track>` 標籤搭配使用。在創建自定義字幕時，開發者可以使用 VTTCue 來添加和修改字幕條目，並將其顯示於視頻中。

## 示例
以下是使用 VTTCue 的基本範例：

```javascript
// 創建新的 VTTCue 物件
let cue = new VTTCue(0, 5, "歡迎收看我們的節目！");

// 設置屬性
cue.line = 0;
cue.position = 50;
cue.align = "middle";

// 將 VTTCue 添加到 track 中
let track = document.querySelector("track");
let textTrack = track.track;
textTrack.addCue(cue);
```

## 解釋
使用 VTTCue 時，開發者需要注意以下幾點：
- **時間格式**: startTime 和 endTime 必須以秒為單位，並且確保 startTime 小於 endTime。
- **添加順序**: 在添加字幕時，確保字幕的時間段不重疊，這樣才能正常顯示。
- **兼容性**: 確保使用的瀏覽器支持 WebVTT 和 VTTCue，因為某些舊版瀏覽器可能不完全支持這些功能。

## 總結
VTTCue 是 JavaScript 中用於管理和顯示 WebVTT 字幕的關鍵物件，能夠提升視頻播放器的可用性和用戶體驗。