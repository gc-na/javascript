<!--
Meta Description: # JavaScript 中的 onratechange 事件詳解 ## 簡介 `onratechange` 事件是 JavaScript 中用於監聽媒體播放速率變化的事件，通常用於 `<audio>` 和 `<video>` 標籤。當用戶改變播放速率時（例如，使用播放速度控制器），該事件會被觸發。...
Meta Keywords: onratechange, video, javascript, mediaelement, audio
-->

# JavaScript 中的 onratechange 事件詳解

## 簡介
`onratechange` 事件是 JavaScript 中用於監聽媒體播放速率變化的事件，通常用於 `<audio>` 和 `<video>` 標籤。當用戶改變播放速率時（例如，使用播放速度控制器），該事件會被觸發。

## 文檔
### 目的
`onratechange` 事件的主要目的是讓開發者能夠監聽和響應媒體元素的播放速率變化。這對於創建更具互動性的媒體體驗尤其重要，例如在視頻播放器中提供自定義的播放速率控制。

### 使用方法
`onratechange` 事件可以通過 JavaScript 的事件監聽器進行註冊。以下是通用的語法：

```javascript
mediaElement.onratechange = function() {
    // 當播放速率變更時執行的代碼
};
```

其中 `mediaElement` 是指 `<audio>` 或 `<video>` 標籤的 DOM 元素。

### 詳細說明
- **事件對象**: 當 `onratechange` 事件被觸發時，事件處理函數會接收到一個事件對象，該對象包含有關事件的信息。
- **速率屬性**: 可以通過 `mediaElement.playbackRate` 屬性獲取當前的播放速率。
- **兼容性**: `onratechange` 事件在大多數現代瀏覽器中都得到支持，但在某些老舊瀏覽器中可能不完全兼容。

## 範例
### 基本用法
以下範例展示了如何使用 `onratechange` 事件來監聽播放速率的變化：

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    var video = document.getElementById("myVideo");
    
    video.onratechange = function() {
        console.log("當前播放速率: " + video.playbackRate);
    };
</script>
```

在這段代碼中，每當用戶改變視頻的播放速率，控制台將打印當前的播放速率。

## 說明
### 常見問題
1. **事件不觸發**: 如果事件未觸發，請確認媒體元素的播放速率確實被改變，並檢查瀏覽器的兼容性。
2. **性能考量**: 在 `onratechange` 事件中執行過於複雜的邏輯可能影響性能，建議將計算邏輯移到其他函數中，並在事件中進行調用。

### 附加說明
- 在使用 `onratechange` 時，請注意用戶的體驗，避免過於頻繁地更新 UI。
- 可以結合其他媒體事件（如 `onplay` 和 `onpause`）來創建更豐富的用戶交互。

## 簡單總結
`onratechange` 事件允許開發者監聽和響應媒體播放速率的變化，為用戶提供更靈活的媒體控制選項。