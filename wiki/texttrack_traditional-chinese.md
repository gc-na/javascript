<!--
Meta Description: # TextTrack: 在JavaScript中使用的文字軌道 ## 概述 `TextTrack` 是HTML5中的一個API，與JavaScript結合使用時，能夠控制和管理視頻或音頻媒體的文字軌道，這些文字軌道通常用於顯示字幕或描述性文本。 ## 文檔 ### 目的 `TextTrack` 目...
Meta Keywords: video, texttrack, tracks, mode, texttracks
-->

# TextTrack: 在JavaScript中使用的文字軌道

## 概述
`TextTrack` 是HTML5中的一個API，與JavaScript結合使用時，能夠控制和管理視頻或音頻媒體的文字軌道，這些文字軌道通常用於顯示字幕或描述性文本。

## 文檔
### 目的
`TextTrack` 目的是為了加強媒體內容的可訪問性和可理解性，特別是在多語言環境下或有聽力障礙的用戶中。它提供了一種方式來添加、操作和顯示字幕和描述。

### 用法
要使用 `TextTrack`，必須首先通過 `HTMLMediaElement` 的 `textTracks` 屬性來訪問媒體元素的文字軌道。每個 `TextTrack` 物件代表一個文字軌道，並提供多種屬性和方法來控制它的行為。

#### 主要屬性
- `kind`: 指定文字軌道的類型，例如 "subtitles"、"captions"、"descriptions" 等。
- `label`: 文字軌道的標籤，通常用於顯示在用戶界面中。
- `language`: 文字軌道的語言標識符，例如 "en" 表示英語。
- `mode`: 控制文字軌道的顯示模式，可能的值有 "disabled"、"hidden" 和 "showing"。

#### 主要方法
- `mode`: 用於設置或獲取當前文字軌道的顯示狀態。
- `addCue()`: 用於向文字軌道中添加一個新的提示（cue）。

### 詳細
在JavaScript中使用 `TextTrack` 時，開發者可以通過以下方式訪問文字軌道：

```javascript
const video = document.querySelector('video');
const tracks = video.textTracks;

// 設置第一個文字軌道為顯示模式
if (tracks.length > 0) {
    tracks[0].mode = 'showing';
}
```

## 示例
### 基本用法
以下是一個添加和顯示文字軌道的簡單示例：

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
    <track kind="subtitles" src="subtitles_zh.vtt" srclang="zh" label="中文">
</video>

<script>
    const video = document.querySelector('video');
    const tracks = video.textTracks;

    // 顯示中文字幕
    for (let i = 0; i < tracks.length; i++) {
        if (tracks[i].language === 'zh') {
            tracks[i].mode = 'showing';
        }
    }
</script>
```

## 解釋
在使用 `TextTrack` 的過程中，開發者可能會遇到一些常見的陷阱：

1. **文字軌道未加載**: 確保在媒體元素的元數據加載後再訪問 `textTracks`，否則可能會得到空的結果。
2. **顯示模式問題**: 如果文字軌道的 `mode` 設置為 `hidden`，將無法顯示相應的文本，即使已正確添加了字幕。

## 一行總結
`TextTrack` 使開發者能夠在HTML5媒體中靈活地管理和顯示字幕和其他文字信息。