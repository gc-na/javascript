<!--
Meta Description: # JavaScript 中的 onseeked 事件：深入了解和使用指南 ## 概述 `onseeked` 事件是 HTMLMediaElement 接口中的一個事件，用於監聽媒體播放（如視頻或音頻）中的播放進度改變。當使用者或程式碼透過播放控件改變了媒體的播放位置時，會觸發此事件。 ## 文件說...
Meta Keywords: onseeked, videoelement, video, javascript, addeventlistener
-->

# JavaScript 中的 onseeked 事件：深入了解和使用指南

## 概述
`onseeked` 事件是 HTMLMediaElement 接口中的一個事件，用於監聽媒體播放（如視頻或音頻）中的播放進度改變。當使用者或程式碼透過播放控件改變了媒體的播放位置時，會觸發此事件。

## 文件說明
`onseeked` 事件的主要目的是提供一種方式來監控媒體的播放進度變更，特別是在用戶手動改變播放時間後。這對於需要更新 UI 或執行某些動作的應用程式非常有用，例如顯示當前播放時間或更新播放狀態。

### 使用方式
要使用 `onseeked` 事件，您可以將其直接設置為 HTMLMediaElement（如 `<video>` 或 `<audio>` 元素）的屬性，或使用 `addEventListener` 方法來監聽此事件。

```javascript
const videoElement = document.getElementById('myVideo');

// 使用 onseeked 屬性
videoElement.onseeked = function() {
    console.log('播放位置已更改！');
};

// 或者使用 addEventListener 方法
videoElement.addEventListener('seeked', function() {
    console.log('播放位置已更改（使用 addEventListener）！');
});
```

## 範例
以下是如何使用 `onseeked` 事件的基本例子：

### HTML
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    您的瀏覽器不支援 video 標籤。
</video>
```

### JavaScript
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.onseeked = function() {
    console.log('播放位置已更改到：' + videoElement.currentTime + ' 秒');
};
```

在此範例中，當使用者拖動視頻進度條改變播放位置時，控制台將顯示當前播放的秒數。

## 解釋
在使用 `onseeked` 事件時，有幾個常見的陷阱需要注意：

1. **事件觸發時機**：`onseeked` 事件只在使用者改變播放時間後觸發，而不包括自動播放或直接設定 `currentTime` 屬性。
   
2. **性能考量**：如果在事件處理程序中執行繁重的計算或 DOM 操作，可能會影響媒體的播放性能，因此建議保持事件處理程序的輕量化。

3. **跨瀏覽器兼容性**：雖然大多數現代瀏覽器都支持 `onseeked` 事件，但在某些舊版瀏覽器中可能不完全支持，因此在實際應用中需進行測試。

## 一句總結
`onseeked` 事件提供了一種有效的方式來監控和響應媒體播放位置的變更，是開發多媒體應用的重要工具。