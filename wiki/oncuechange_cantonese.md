<!--
Meta Description: # JavaScript oncuechange 事件：全面指南 ## 簡介 `oncuechange` 是一個與 HTML5 視頻和音頻元素相關的事件，用於當媒體的顯示字幕（即“cue”）變更時觸發的事件。在 JavaScript 中，開發者可以利用此事件來增強媒體播放體驗，例如顯示即時字幕或進行...
Meta Keywords: oncuechange, activecues, video, cuechange, const
-->

# JavaScript oncuechange 事件：全面指南

## 簡介
`oncuechange` 是一個與 HTML5 視頻和音頻元素相關的事件，用於當媒體的顯示字幕（即“cue”）變更時觸發的事件。在 JavaScript 中，開發者可以利用此事件來增強媒體播放體驗，例如顯示即時字幕或進行用戶互動。

## 文檔
### 目的
`oncuechange` 事件的主要目的是讓開發者能夠在媒體播放過程中監聽並回應字幕的變化。這對於需要即時反饋的應用程序特別重要，例如教育平台或娛樂應用。

### 用法
要使用 `oncuechange` 事件，您需要將其綁定到相應的媒體元素（如 `<video>` 或 `<audio>`）。事件會在顯示的字幕變更時觸發，開發者可以通過添加事件監聽器來處理該事件。

以下是一個基本的語法示例：
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.addEventListener('cuechange', function() {
    const activeCues = this.textTracks[0].activeCues;
    if (activeCues.length > 0) {
        console.log('當前字幕:', activeCues[0].text);
    }
});
```

### 詳細說明
- **事件觸發**：當媒體元素的字幕改變時，`oncuechange` 事件會被觸發。
- **文本軌道（Text Track）**：必須確保媒體元素擁有至少一個文本軌道，否則事件將不會觸發。
- **activeCues**：開發者可以訪問當前顯示的字幕（active cues），以獲取相關信息。
- **兼容性**：檢查不同瀏覽器對 `cuechange` 的支持情況，確保功能在所有目標瀏覽器中正常運行。

## 示例
以下是一個簡單的例子，展示如何使用 `oncuechange` 事件來顯示當前字幕：
```html
<video id="myVideo" controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
  Your browser does not support the video tag.
</video>

<script>
  const videoElement = document.getElementById('myVideo');

  videoElement.addEventListener('cuechange', function() {
      const cues = this.textTracks[0].activeCues;
      if (cues.length > 0) {
          console.log('當前字幕:', cues[0].text);
      }
  });
</script>
```

## 說明
- **常見問題**：如果 `cuechange` 事件未觸發，請檢查媒體元素是否正確加載字幕以及是否存在活動的文本軌道。
- **性能影響**：在高頻率觸發的事件中，過度處理可能導致性能問題，建議使用防抖（debounce）技術來優化性能。
- **用戶體驗**：合理使用 `cuechange` 事件可以提升用戶對媒體內容的理解，特別是對於語言學習者或聽障人士。

## 一句話總結
`oncuechange` 是一個強大的事件，用於監聽和響應 HTML5 媒體元素中字幕的變化，幫助提升用戶體驗。