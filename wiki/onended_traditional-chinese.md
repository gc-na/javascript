<!--
Meta Description: # JavaScript 的 onended 事件詳解 ## 概述 `onended` 是一個與音頻和視頻播放相關的事件，當媒體元素播放結束後觸發。它常用於音頻和視頻的控制，讓開發者能夠在媒體播放完成時執行特定的操作。 ## 文檔 ### 目的 `onended` 事件的主要用途是讓開發者可以在音頻...
Meta Keywords: onended, audio, audioelement, javascript, myaudio
-->

# JavaScript 的 onended 事件詳解

## 概述
`onended` 是一個與音頻和視頻播放相關的事件，當媒體元素播放結束後觸發。它常用於音頻和視頻的控制，讓開發者能夠在媒體播放完成時執行特定的操作。

## 文檔
### 目的
`onended` 事件的主要用途是讓開發者可以在音頻或視頻播放結束時執行一些回調函數。這對於需要在媒體播放完畢後進行下一步操作的應用特別有用，如自動播放下一曲音樂或顯示播放結束的訊息。

### 使用方式
`onended` 事件通常用於 HTML5 的 `<audio>` 和 `<video>` 元素中。可以通過 JavaScript 將事件處理器附加到這些媒體元素上。

```javascript
const audioElement = document.getElementById('myAudio');

audioElement.onended = function() {
    console.log('音樂播放完畢！');
};
```

### 詳細信息
- **事件類型**: `Event`
- **觸發條件**: 當音頻或視頻播放完成時。
- **支持的瀏覽器**: 主要現代瀏覽器都支持該事件，包括 Chrome、Firefox、Safari 和 Edge。

## 範例
### 基本用法
以下是使用 `onended` 事件的基本範例：

```html
<audio id="myAudio" controls>
    <source src="song.mp3" type="audio/mpeg">
    您的瀏覽器不支持音頻元素。
</audio>

<script>
    const audioElement = document.getElementById('myAudio');

    audioElement.onended = function() {
        alert('音樂播放結束了！');
    };
</script>
```

在這個範例中，當音樂播放結束時，將會彈出一個提示框。

## 解釋
### 常見陷阱和注意事項
- **事件未觸發**: 確保媒體元素的 `src` 屬性正確設置，並且媒體文件可正常加載。如果媒體文件無法播放，則 `onended` 事件不會觸發。
- **多次綁定**: 如果多次綁定 `onended` 事件，會導致前面的綁定被覆蓋。可以使用 `addEventListener` 方法來避免這個問題。

### 附加說明
在某些情況下，`onended` 事件可能會因用戶交互（如點擊暫停）而未能觸發，因此在整體媒體控制邏輯中需要考慮到用戶的行為。

## 一句總結
`onended` 事件讓開發者能夠在音頻或視頻播放結束時執行自定義操作，增強用戶體驗。