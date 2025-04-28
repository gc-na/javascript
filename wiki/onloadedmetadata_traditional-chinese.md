<!--
Meta Description: # onloadedmetadata 事件在 JavaScript 中的應用 ## 摘要 `onloadedmetadata` 是一個 JavaScript 事件，用於當媒體元素（如 `<video>` 或 `<audio>`）的元數據加載完成時觸發，這些元數據通常包括媒體的持續時間、尺寸及其他相關...
Meta Keywords: onloadedmetadata, audio, video, javascript, script
-->

# onloadedmetadata 事件在 JavaScript 中的應用

## 摘要
`onloadedmetadata` 是一個 JavaScript 事件，用於當媒體元素（如 `<video>` 或 `<audio>`）的元數據加載完成時觸發，這些元數據通常包括媒體的持續時間、尺寸及其他相關資訊。

## 文檔
`onloadedmetadata` 事件是一個 HTMLMediaElement 事件，專門用於處理媒體文件的元數據加載。當媒體元素的元數據（如音頻或視頻檔案的長度和尺寸）被加載後，這個事件會被觸發，允許開發者在此時進行相應的操作。

### 目的
此事件的主要用途是讓開發者能夠在媒體元數據可用後進行操作，例如更新 UI、啟用播放按鈕或顯示媒體的持續時間。

### 使用方法
要使用 `onloadedmetadata` 事件，可以直接在媒體元素中指定事件處理函數，或使用 JavaScript 來添加事件監聽器。

#### 語法示例：
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    您的瀏覽器不支援視頻標籤。
</video>

<script>
    const video = document.getElementById('myVideo');
    video.onloadedmetadata = function() {
        console.log(`影片長度: ${video.duration}秒`);
    };
</script>
```

## 示例
這裡有一個簡單的示例，展示如何使用 `onloadedmetadata` 來獲取視頻的長度：

```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    您的瀏覽器不支援音頻標籤。
</audio>

<script>
    const audio = document.getElementById('myAudio');
    audio.onloadedmetadata = function() {
        alert(`音頻長度: ${audio.duration}秒`);
    };
</script>
```

## 解釋
在使用 `onloadedmetadata` 事件時，有幾個常見的注意事項：

1. **事件觸發時機**：`onloadedmetadata` 事件僅在媒體元素的元數據加載完成後觸發。如果媒體文件未正確加載，則此事件不會觸發。
   
2. **瀏覽器兼容性**：大多數現代瀏覽器均支持此事件，但在某些舊版瀏覽器中可能存在問題。開發者應該檢查目標瀏覽器的兼容性。

3. **多次觸發**：在某些情況下，如果媒體元素的源被更改，該事件將再次觸發。開發者應根據需求適當處理這種情況。

## 總結
`onloadedmetadata` 事件是 JavaScript 中用於處理媒體元素元數據加載的關鍵事件，適合用來獲取媒體的相關信息並進行後續操作。