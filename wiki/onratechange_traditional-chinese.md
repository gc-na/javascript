<!--
Meta Description: # onratechange 事件在 JavaScript 中的應用 ## 概述 `onratechange` 事件是 JavaScript 中一個重要的事件，主要用於監聽媒體元素（如 `<video>` 和 `<audio>`）播放速率的變化。當用戶調整播放速率時，此事件會被觸發，讓開發者能夠進行...
Meta Keywords: video, onratechange, javascript, html, handleratechange
-->

# onratechange 事件在 JavaScript 中的應用

## 概述
`onratechange` 事件是 JavaScript 中一個重要的事件，主要用於監聽媒體元素（如 `<video>` 和 `<audio>`）播放速率的變化。當用戶調整播放速率時，此事件會被觸發，讓開發者能夠進行相應的處理。

## 文檔
`onratechange` 事件的目的在於提供一種方式來監測媒體播放的速率變化。當播放速率被用戶調整時，該事件會被觸發，並且可以通過事件處理器來獲取當前的播放速率。這對於需要根據播放速率變化來調整界面或執行其他邏輯的應用程序來說非常有用。

### 使用方式
`onratechange` 事件可以透過以下幾種方式來使用：

1. **HTML 屬性**：
   直接在媒體元素中使用 `onratechange` 屬性來指定事件處理器。
   ```html
   <video onratechange="handleRateChange()">
       <source src="movie.mp4" type="video/mp4">
   </video>
   ```

2. **JavaScript 事件監聽器**：
   使用 JavaScript 來添加事件監聽器。
   ```javascript
   const video = document.querySelector('video');
   video.addEventListener('ratechange', handleRateChange);
   ```

### 事件處理器
事件處理器會接收到一個事件對象，該對象包含了與事件相關的資訊，例如當前的播放速率。可以通過 `event.target.playbackRate` 獲取當前播放速率：

```javascript
function handleRateChange(event) {
    console.log('當前播放速率:', event.target.playbackRate);
}
```

## 範例
以下是一個使用 `onratechange` 事件的基本範例：

```html
<!DOCTYPE html>
<html>
<head>
    <title>Rate Change Example</title>
</head>
<body>
    <video controls width="600" onratechange="handleRateChange()">
        <source src="movie.mp4" type="video/mp4">
    </video>

    <script>
        function handleRateChange() {
            const video = document.querySelector('video');
            console.log('當前播放速率:', video.playbackRate);
        }
    </script>
</body>
</html>
```

## 解釋
在使用 `onratechange` 事件時，有幾個常見的陷阱和注意事項：

1. **不支持的瀏覽器**：某些舊版瀏覽器可能不完全支持 `onratechange` 事件，確保在開發時進行兼容性測試。
2. **多次觸發**：當用戶不斷調整播放速率時，該事件可能會被觸發多次，因此在事件處理器中應適當處理多次觸發的情況。
3. **初始化速率**：當媒體元素被創建時，初始播放速率不會觸發 `onratechange` 事件，只會在用戶調整速率後觸發。

## 總結
`onratechange` 事件是 JavaScript 中一個用於監控媒體播放速率變化的重要事件，能夠幫助開發者實現更靈活的媒體播放控制功能。