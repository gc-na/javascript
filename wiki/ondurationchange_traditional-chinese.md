<!--
Meta Description: # JavaScript 的 ondurationchange 事件 ## 概述 `ondurationchange` 是一個在媒體元素（如 `<audio>` 和 `<video>`）的持續時間變更時觸發的事件。這個事件可用於監控媒體的持續時間，並在其變更時執行相應的回調函數。 ## 文檔 ###...
Meta Keywords: ondurationchange, audio, video, script, function
-->

# JavaScript 的 ondurationchange 事件

## 概述
`ondurationchange` 是一個在媒體元素（如 `<audio>` 和 `<video>`）的持續時間變更時觸發的事件。這個事件可用於監控媒體的持續時間，並在其變更時執行相應的回調函數。

## 文檔
### 目的
`ondurationchange` 事件主要用於檢測媒體元素的持續時間是否發生變化。這在處理多媒體播放時非常有用，因為媒體的持續時間可能因為編碼或其他因素而變更。

### 使用方法
要使用 `ondurationchange` 事件，您需要將其添加到媒體元素的事件監聽器中。當持續時間改變時，指定的事件處理函數將被調用。

### 語法
```javascript
mediaElement.ondurationchange = function() {
    // 當持續時間改變時執行的代碼
};
```

### 參數
- `mediaElement`：可以是 `<audio>` 或 `<video>` 標籤的 DOM 對象。

## 範例
以下是如何使用 `ondurationchange` 事件的基本示例：

### 例子 1: 基本用法
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    您的瀏覽器不支持 video 標籤。
</video>

<script>
    const video = document.getElementById('myVideo');

    video.ondurationchange = function() {
        console.log('視頻的持續時間已改變為: ' + video.duration + ' 秒');
    };
</script>
```

### 例子 2: 監控音頻持續時間
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    您的瀏覽器不支持 audio 標籤。
</audio>

<script>
    const audio = document.getElementById('myAudio');

    audio.ondurationchange = function() {
        alert('音頻的持續時間已改變為: ' + audio.duration + ' 秒');
    };
</script>
```

## 解釋
### 常見陷阱與注意事項
- **不支援的瀏覽器**：某些老舊的瀏覽器可能不支援 `ondurationchange` 事件，因此在使用之前應進行相容性檢查。
- **異步加載**：當媒體文件異步加載時，持續時間可能在文件完全加載之前就已經變更，因此建議在開始播放之前檢查持續時間。
- **多媒體文件格式**：不同格式的媒體文件在持續時間計算上可能會有所不同，確保使用的媒體格式是廣泛支援的。

## 一行總結
`ondurationchange` 事件允許開發者在媒體元素的持續時間變更時執行特定的代碼，使得多媒體處理更為靈活。