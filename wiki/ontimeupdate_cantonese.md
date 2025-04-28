<!--
Meta Description: # JavaScript 事件：ontimeupdate 的詳細指南 ## 摘要 `ontimeupdate` 是一個在 HTML5 視頻和音頻元素中使用的事件，當媒體播放時間發生變化時會觸發。這使得開發者可以實時獲取媒體播放進度，以便進行相應的操作。 ## 文檔 ### 目的 `ontimeupd...
Meta Keywords: ontimeupdate, video, timedisplay, html5, 當媒體播放時間更新時
-->

# JavaScript 事件：ontimeupdate 的詳細指南

## 摘要
`ontimeupdate` 是一個在 HTML5 視頻和音頻元素中使用的事件，當媒體播放時間發生變化時會觸發。這使得開發者可以實時獲取媒體播放進度，以便進行相應的操作。

## 文檔
### 目的
`ontimeupdate` 事件在媒體播放過程中，當當前播放時間的變化達到一定的時間間隔時被觸發。這對於需要實現進度條更新、顯示當前播放時間或進行其他實時更新的應用場景非常有用。

### 用法
要使用 `ontimeupdate`，您首先需要獲取一個媒體元素（如 `<audio>` 或 `<video>`），然後為其添加事件監聽器。當媒體播放時間更新時，您可以執行相應的回調函數。

### 詳細信息
- **事件類型**: `timeupdate`
- **觸發條件**: 媒體元素的播放時間發生變化，包括播放、暫停和快進等操作。
- **可用屬性**: 在事件處理器中，可以通過 `currentTime` 屬性獲取當前播放時間（以秒為單位）。

## 示例
以下是使用 `ontimeupdate` 的基本範例：

```html
<video id="myVideo" width="400" controls>
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>

<p id="timeDisplay">當前時間: 0</p>

<script>
  const video = document.getElementById('myVideo');
  const timeDisplay = document.getElementById('timeDisplay');

  video.ontimeupdate = function() {
    timeDisplay.textContent = '當前時間: ' + Math.floor(video.currentTime);
  };
</script>
```

在這個例子中，當媒體播放時間更新時，會實時顯示當前播放的秒數。

## 解釋
在使用 `ontimeupdate` 時，有幾個常見的注意事項：
1. **性能影響**: 由於這個事件會頻繁觸發（通常每秒多次），在事件處理器中執行重計算或大型操作可能會導致性能問題。建議使用防抖（debounce）或節流（throttle）技巧來優化性能。
2. **相容性**: 確保您的應用在所有主流瀏覽器中都進行測試，以避免相容性問題。
3. **事件監聽**: 可以使用 `addEventListener` 方法來添加事件監聽器，這樣可以讓您的代碼更加模組化。

## 一句總結
`ontimeupdate` 事件允許開發者在媒體播放過程中實時獲取和處理播放進度，以提升用戶體驗。