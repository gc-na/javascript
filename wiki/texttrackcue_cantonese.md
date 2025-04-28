<!--
Meta Description: # TextTrackCue：JavaScript 中的文本轨迹提示 ## 概述 `TextTrackCue` 是一個用於描述媒體字幕的 JavaScript 介面。它提供了一種方式來定義和操作視訊或音訊中顯示的字幕內容，確保使用者能夠在觀看媒體時理解其中的對話和音效。 ## 文檔 ### 目的 `...
Meta Keywords: texttrackcue, cue, javascript, video, track
-->

# TextTrackCue：JavaScript 中的文本轨迹提示

## 概述
`TextTrackCue` 是一個用於描述媒體字幕的 JavaScript 介面。它提供了一種方式來定義和操作視訊或音訊中顯示的字幕內容，確保使用者能夠在觀看媒體時理解其中的對話和音效。

## 文檔
### 目的
`TextTrackCue` 的主要目的是提供一種結構化的方式來表示字幕或文本提示。這使得開發者能夠更靈活地管理和控制媒體播放時的字幕顯示。

### 使用方法
`TextTrackCue` 物件通常與 HTML5 的 `<track>` 標籤一起使用。當你在媒體元素中添加字幕時，這個物件幫助定義每個字幕的開始時間、結束時間和內容。

### 屬性
- **startTime**: 字幕顯示的開始時間（以秒為單位）。
- **endTime**: 字幕顯示的結束時間（以秒為單位）。
- **text**: 實際顯示的文本內容。
- **id**: 字幕的唯一標識符（可選）。

### 方法
`TextTrackCue` 並不包含額外的方法，但可以與 `TextTrack` 物件的相關方法一起使用，例如 `addCue()` 和 `removeCue()`。

## 範例
以下是一個基本的範例，展示如何使用 `TextTrackCue`：

```javascript
// 創建一個新的 TextTrackCue 實例
const cue = new TextTrackCue(0, 5, "這是一個簡單的字幕");

// 獲取屬性
console.log(cue.startTime); // 輸出: 0
console.log(cue.endTime);   // 輸出: 5
console.log(cue.text);      // 輸出: "這是一個簡單的字幕"

// 假設有一個 video 元素和相應的 textTrack
const video = document.querySelector('video');
const track = video.addTextTrack('subtitles', '中文字幕', 'zh');

// 添加字幕
track.addCue(cue);
```

## 解釋
使用 `TextTrackCue` 時，有一些常見的陷阱和注意事項：

- **時間範圍重疊**: 確保不同的 `TextTrackCue` 之間沒有時間重疊，否則可能導致顯示混亂。
- **語言和格式**: 確保字幕的語言和格式正確，這樣使用者才能正確理解內容。
- **瀏覽器支援**: 雖然大多數現代瀏覽器都支援 `TextTrackCue`，但在某些舊版瀏覽器中可能無法正常工作。

## 一句總結
`TextTrackCue` 是 JavaScript 中用於操作媒體字幕的強大工具，提供靈活的字幕管理功能。