<!--
Meta Description: # JavaScript 中的 onloadeddata 事件：全面指南 ## 概述 `onloadeddata` 是一個在 HTML5 中引入的事件，用於音頻和視頻元素，當媒體的當前播放位置的數據已經加載並可以開始播放時觸發。這對於處理媒體加載及播放狀態非常有用。 ## 文檔 ### 目的 `on...
Meta Keywords: onloadeddata, video, html, myvideo, mp4
-->

# JavaScript 中的 onloadeddata 事件：全面指南

## 概述
`onloadeddata` 是一個在 HTML5 中引入的事件，用於音頻和視頻元素，當媒體的當前播放位置的數據已經加載並可以開始播放時觸發。這對於處理媒體加載及播放狀態非常有用。

## 文檔
### 目的
`onloadeddata` 事件的主要目的是通知開發者媒體數據已經加載，並且可以開始播放。這對於需要在媒體播放前執行某些操作的應用程序來說特別重要。

### 使用方式
`onloadeddata` 事件可以通過添加事件監聽器或直接在 HTML 標籤中設置來使用。下面是如何使用的示例：

#### 透過 JavaScript 設定事件監聽器
```javascript
const videoElement = document.getElementById('myVideo');
videoElement.addEventListener('loadeddata', function() {
    console.log('媒體數據已加載，可以開始播放。');
});
```

#### 透過 HTML 標籤設置
```html
<video id="myVideo" onloadeddata="mediaLoaded()">
    <source src="video.mp4" type="video/mp4">
    你的瀏覽器不支援視頻標籤。
</video>

<script>
function mediaLoaded() {
    console.log('媒體數據已加載，可以開始播放。');
}
</script>
```

## 示例
這裡有一個完整的示例，展示如何使用 `onloadeddata` 事件來控制視頻播放：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onloadeddata 示例</title>
</head>
<body>
    <video id="myVideo" width="320" height="240" controls>
        <source src="movie.mp4" type="video/mp4">
        你的瀏覽器不支援視頻標籤。
    </video>

    <script>
        const video = document.getElementById('myVideo');
        video.addEventListener('loadeddata', () => {
            console.log('媒體數據已加載，視頻即將播放。');
            video.play(); // 自動播放視頻
        });
    </script>
</body>
</html>
```

## 解釋
### 常見陷阱
- **事件未觸發**: 如果媒體數據沒有完全加載，`onloadeddata` 將不會被觸發，這可能導致開發者誤以為有錯誤發生。
- **多次觸發**: 如果媒體元素的來源改變，可能會多次觸發 `onloadeddata` 事件，因此需要適當管理事件處理邏輯以避免重複執行不必要的操作。

### 額外說明
- `onloadeddata` 事件在每次加載新數據時都會被觸發，這對於需要動態更新媒體源的應用程序特別有用。
- 此事件僅在 `<audio>` 或 `<video>` 標籤中有效。

## 一行總結
`onloadeddata` 事件用於通知當前媒體數據已經加載並可開始播放，對於音頻和視頻元素的控制至關重要。