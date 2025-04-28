<!--
Meta Description: # JavaScript ontimeupdate 事件：即時更新媒體播放狀態 ## 概述 `ontimeupdate` 是一個在 JavaScript 中與 HTML5 媒體元素（如 `<audio>` 和 `<video>`）相關的事件。當媒體播放位置更新時（例如，使用者拖動進度條或媒體自動播放...
Meta Keywords: video, ontimeupdate, javascript, addeventlistener, function
-->

# JavaScript ontimeupdate 事件：即時更新媒體播放狀態

## 概述
`ontimeupdate` 是一個在 JavaScript 中與 HTML5 媒體元素（如 `<audio>` 和 `<video>`）相關的事件。當媒體播放位置更新時（例如，使用者拖動進度條或媒體自動播放），這個事件會被觸發，允許開發者獲取當前播放時間並進行相應的處理。

## 文檔
### 目的
`ontimeupdate` 事件的主要目的是讓開發者在媒體播放狀態改變時執行特定的代碼，這對於創建互動式媒體播放器或更新用戶界面特別重要。

### 使用方式
`ontimeupdate` 事件可以直接在媒體元素上使用，也可以通過 JavaScript 代碼來添加事件監聽器。以下是基本的語法：

```javascript
mediaElement.ontimeupdate = function() {
    // 事件處理代碼
};
```

或者使用 `addEventListener`：

```javascript
mediaElement.addEventListener('timeupdate', function() {
    // 事件處理代碼
});
```

### 詳細說明
- **事件觸發**：當媒體的播放位置變化時，`ontimeupdate` 事件會被觸發。可以在事件處理函數中獲取當前播放時間，例如 `mediaElement.currentTime`。
- **支持的媒體元素**：`ontimeupdate` 事件可用於 `<audio>` 和 `<video>` 元素。
- **頻率**：該事件會在媒體播放過程中多次觸發，因此在事件處理程序中應謹慎處理性能問題。

## 範例
### 基本用法
以下是一個簡單的示例，展示如何在 `<video>` 元素上使用 `ontimeupdate` 事件：

```html
<video id="myVideo" width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  您的瀏覽器不支持視頻標籤。
</video>

<script>
  const video = document.getElementById('myVideo');
  
  video.ontimeupdate = function() {
    console.log('當前播放時間: ' + video.currentTime + '秒');
  };
</script>
```

### 使用 `addEventListener`
也可以使用 `addEventListener` 方法來監聽 `ontimeupdate` 事件：

```html
<video id="myVideo" width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  您的瀏覽器不支持視頻標籤。
</video>

<script>
  const video = document.getElementById('myVideo');
  
  video.addEventListener('timeupdate', function() {
    console.log('當前播放時間: ' + video.currentTime + '秒');
  });
</script>
```

## 解釋
### 常見陷阱
- **性能問題**：由於 `ontimeupdate` 事件會頻繁觸發，應避免在事件處理器中執行高開銷的操作。可以考慮使用節流（throttling）或防抖（debouncing）技術來優化性能。
- **不支持的瀏覽器**：舊版瀏覽器可能不支持 HTML5 媒體元素和相應的事件，開發者應考慮使用合適的回退機制。

## 一句總結
`ontimeupdate` 事件允許開發者在媒體播放時間變化時執行特定代碼，以增強用戶互動體驗。