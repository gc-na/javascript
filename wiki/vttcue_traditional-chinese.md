<!--
Meta Description: # VTTCue：JavaScript 的 WebVTT 字幕物件 ## 簡介 VTTCue 是一個用於處理 WebVTT（Web Video Text Tracks）字幕的 JavaScript 物件，主要用於視頻播放時的文本顯示。它提供了字幕的時間範圍、文本內容及其樣式設定，使得開發者可以靈活地...
Meta Keywords: vttcue, javascript, video, text, let
-->

# VTTCue：JavaScript 的 WebVTT 字幕物件

## 簡介
VTTCue 是一個用於處理 WebVTT（Web Video Text Tracks）字幕的 JavaScript 物件，主要用於視頻播放時的文本顯示。它提供了字幕的時間範圍、文本內容及其樣式設定，使得開發者可以靈活地添加和管理視頻中的字幕。

## 文檔
### 目的
VTTCue 物件的目的是為了使開發者能夠在 HTML5 視頻中輕鬆地創建和管理字幕。它能夠定義字幕的開始和結束時間，以及顯示的文本和樣式屬性。

### 使用方法
要使用 VTTCue，首先需確保已經在頁面中引入了 HTML5 視頻元素。接著，可以通過以下方式創建一個 VTTCue 物件：

```javascript
let cue = new VTTCue(startTime, endTime, text, settings);
```

- `startTime`：字幕開始顯示的時間（以秒為單位）。
- `endTime`：字幕結束顯示的時間（以秒為單位）。
- `text`：顯示的字幕內容。
- `settings`：可選的參數，用於設置字幕的樣式。

### 詳細信息
VTTCue 物件提供了一系列屬性和方法，讓開發者可以更靈活地操作字幕：

- **屬性**：
  - `startTime`：獲取或設置字幕的開始時間。
  - `endTime`：獲取或設置字幕的結束時間。
  - `text`：獲取或設置顯示的字幕文本。
  - `line`、`position`、`align`：用於設置字幕的顯示位置和對齊方式。

- **方法**：
  - `getCueAsHTML()`：返回包含字幕的 HTML 字符串。

## 範例
以下是 VTTCue 的基本使用範例：

```javascript
// 創建一個新的 VTTCue
let cue1 = new VTTCue(0, 5, "歡迎來到我們的視頻！");

// 添加到 video track 中
let video = document.querySelector("video");
let track = video.addTextTrack("subtitles", "中文字幕", "zh");
track.addCue(cue1);
```

在這個範例中，我們創建了一個從 0 到 5 秒顯示的字幕，並將其添加到視頻中。

## 解釋
使用 VTTCue 時需注意以下幾點：

1. **時間格式**：確保 `startTime` 和 `endTime` 的設置正確，否則字幕可能不會正確顯示。
2. **重疊問題**：如果多個字幕的時間範圍重疊，只有最後添加的字幕會顯示，需妥善管理字幕的時間。
3. **樣式設置**：在設置樣式時，需確保所用的 CSS 屬性支持在字幕中正確顯示。

## 一句總結
VTTCue 是一個強大的 JavaScript 物件，用於創建和管理 HTML5 視頻中的 WebVTT 字幕。