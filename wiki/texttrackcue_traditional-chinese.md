<!--
Meta Description: # TextTrackCue：JavaScript 中的文本軌道提示 ## 簡介 `TextTrackCue` 是一個 JavaScript 物件，用於表示在視頻或音頻播放中顯示的文字提示。它通常與 HTML5 的 `<track>` 元素一起使用，能夠提供字幕、音訊描述或其他文本信息，幫助用戶更好...
Meta Keywords: texttrackcue, javascript, cue, starttime, endtime
-->

# TextTrackCue：JavaScript 中的文本軌道提示

## 簡介
`TextTrackCue` 是一個 JavaScript 物件，用於表示在視頻或音頻播放中顯示的文字提示。它通常與 HTML5 的 `<track>` 元素一起使用，能夠提供字幕、音訊描述或其他文本信息，幫助用戶更好地理解媒體內容。

## 文檔
### 目的
`TextTrackCue` 的主要目的是在多媒體播放過程中顯示文本提示，這對於聽障人士或需要不同語言支持的觀眾尤其重要。它能夠與視頻或音頻的時間軸同步，確保文本在適當的時間顯示。

### 使用方法
要使用 `TextTrackCue`，需要在 JavaScript 中創建一個新的 `TextTrackCue` 實例，通常在已經存在的 `TextTrack` 中進行操作。語法如下：

```javascript
let cue = new TextTrackCue(startTime, endTime, text);
```

- `startTime`：提示開始顯示的時間（以秒為單位）。
- `endTime`：提示結束顯示的時間（以秒為單位）。
- `text`：要顯示的文本内容。

### 屬性
- `startTime`：返回提示開始顯示的時間點。
- `endTime`：返回提示結束顯示的時間點。
- `text`：返回提示的文本內容。
- `track`：返回與該提示相關聯的 `TextTrack` 物件。

### 方法
- `getCueAsHTML()`：返回提示的 HTML 版本，在某些情況下可用於更好的格式化。

## 示例
以下是創建 `TextTrackCue` 的基本示例：

```javascript
// 創建一個新的 TextTrackCue
let cue = new TextTrackCue(0, 5, "歡迎來到我們的視頻！");

// 獲取提示的屬性
console.log(cue.startTime); // 輸出: 0
console.log(cue.endTime);   // 輸出: 5
console.log(cue.text);      // 輸出: 歡迎來到我們的視頻！

// 獲取 HTML 格式的提示
let cueAsHTML = cue.getCueAsHTML();
console.log(cueAsHTML); // 輸出: <span>歡迎來到我們的視頻！</span>
```

## 解釋
使用 `TextTrackCue` 時應注意以下常見問題：
- 确保 `startTime` 和 `endTime` 的值正確，`startTime` 必須小於 `endTime`。
- 在播放媒體時，確保文本提示與媒體的進度同步。
- 在使用 `getCueAsHTML()` 方法時，注意 HTML 內容可能需要特別處理以避免 XSS 攻擊。

## 一句總結
`TextTrackCue` 是一個用於在多媒體播放中顯示文本提示的 JavaScript 物件，能夠增強用戶的觀看體驗。