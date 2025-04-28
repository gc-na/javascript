<!--
Meta Description: # onloadedmetadata 事件在 JavaScript 中的應用 ## 概述 `onloadedmetadata` 是一個網頁媒體元素事件，當媒體的元數據（例如持續時間和尺寸等）已經加載完成後觸發。這個事件在處理音頻和視頻時特別有用，因為它允許開發者在媒體準備好可以播放時執行特定的操作。...
Meta Keywords: video, onloadedmetadata, audio, script, html
-->

# onloadedmetadata 事件在 JavaScript 中的應用

## 概述
`onloadedmetadata` 是一個網頁媒體元素事件，當媒體的元數據（例如持續時間和尺寸等）已經加載完成後觸發。這個事件在處理音頻和視頻時特別有用，因為它允許開發者在媒體準備好可以播放時執行特定的操作。

## 文檔
`onloadedmetadata` 事件主要針對 `<audio>` 和 `<video>` 標籤。當媒體元素的元數據加載完成後，此事件會被觸發，這意味著我們可以獲取有關媒體的資訊，如持續時間和視頻的寬高比。這對於想要自動調整播放器界面或進行其他初始化操作的開發者來說非常重要。

### 用法
要使用 `onloadedmetadata`，可以通過直接在 HTML 元素中設置事件處理器，或者在 JavaScript 中添加事件監聽器。以下是基本的用法示例：

```html
<video id="myVideo" controls>
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<script>
  const video = document.getElementById('myVideo');
  video.onloadedmetadata = function() {
    console.log('元數據已加載');
    console.log('持續時間: ' + video.duration + '秒');
  };
</script>
```

## 範例
### 基本使用示例
以下示例展示了如何使用 `onloadedmetadata` 事件來獲取視頻的持續時間：

```html
<video id="myVideo" controls>
  <source src="example.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<script>
  const videoElement = document.getElementById('myVideo');

  videoElement.onloadedmetadata = function() {
    console.log('視頻持續時間: ' + videoElement.duration + '秒');
  };
</script>
```

### 使用事件監聽器
你也可以使用 `addEventListener` 方法來添加 `onloadedmetadata` 事件：

```html
<audio id="myAudio" controls>
  <source src="audio.mp3" type="audio/mpeg">
  Your browser does not support the audio tag.
</audio>

<script>
  const audioElement = document.getElementById('myAudio');

  audioElement.addEventListener('loadedmetadata', function() {
    console.log('音頻持續時間: ' + audioElement.duration + '秒');
  });
</script>
```

## 解釋
在使用 `onloadedmetadata` 時，開發者應注意以下幾點：

1. **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持此事件，但在一些舊版本的瀏覽器中可能不支持。
2. **多次觸發**：此事件在每次媒體元素的元數據加載時會被觸發，因此如果你多次重載相同的媒體，這個事件會重複觸發。
3. **媒體格式**：確保所用的媒體格式受支持，否則元數據將不會加載，事件也不會觸發。

## 一句話總結
`onloadedmetadata` 事件在 JavaScript 中用於獲取媒體元素的元數據，並在這些數據加載完成後執行特定操作。