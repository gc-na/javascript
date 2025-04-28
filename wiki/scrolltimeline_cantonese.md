<!--
Meta Description: # ScrollTimeline：JavaScript 的滾動時間線功能 ## 簡介 ScrollTimeline 是一個新的 JavaScript API，旨在使開發者能夠基於用戶的滾動行為創建動畫和過渡效果。這個功能提供了一種簡單的方式來將滾動位置直接與動畫的時間進行綁定，從而提升用戶體驗。 #...
Meta Keywords: scrolltimeline, timeline, javascript, scroll, start
-->

# ScrollTimeline：JavaScript 的滾動時間線功能

## 簡介
ScrollTimeline 是一個新的 JavaScript API，旨在使開發者能夠基於用戶的滾動行為創建動畫和過渡效果。這個功能提供了一種簡單的方式來將滾動位置直接與動畫的時間進行綁定，從而提升用戶體驗。

## 文檔
### 目的
ScrollTimeline 的主要目的是提供一種將滾動事件與動畫進行同步的手段。它允許開發者根據用戶在頁面上滾動的進度來調整動畫的進度，從而創建更具互動性的網站。

### 使用方法
要使用 ScrollTimeline，首先需要確保瀏覽器支持這個 API。接著，你可以按照以下步驟進行設置：

1. **創建 ScrollTimeline 實例**：
   ```javascript
   const timeline = new ScrollTimeline({
       scrollRequests: [{
           target: document.querySelector('#scroll-container'),
           start: 'self-start',
           end: 'self-end'
       }]
   });
   ```

2. **將 Timeline 應用於動畫**：
   使用 CSS 動畫或 JavaScript 動畫庫時，可以將 ScrollTimeline 與其結合，達到基於滾動的效果。

   ```css
   .animate {
       animation: fadeIn 1s;
       animation-timeline: timeline;
   }
   ```

### 詳細信息
ScrollTimeline 允許開發者定義滾動的開始和結束點，並可以使用這些信息來計算當前的動畫狀態。這使得創建基於滾動的動畫變得簡單且高效。它支持多種滾動容器，並且可與 CSS 動畫和 JavaScript 動畫庫兼容使用。

## 示例
### 基本用法範例
以下是一個簡單的範例，展示如何使用 ScrollTimeline 來隨著滾動顯示和隱藏一個元素。

```html
<div id="scroll-container" style="height: 200vh; overflow-y: scroll;">
    <div class="animate">隨滾動而顯示的內容</div>
</div>

<script>
   const timeline = new ScrollTimeline({
       scrollRequests: [{
           target: document.querySelector('#scroll-container'),
           start: 'self-start',
           end: 'self-end'
       }]
   });

   document.querySelector('.animate').animate([
       { opacity: 0 },
       { opacity: 1 }
   ], {
       timeline: timeline,
       duration: 1000
   });
</script>
```

## 解釋
### 常見問題
- **不支持的瀏覽器**：不是所有瀏覽器都支持 ScrollTimeline，因此在使用之前，開發者應檢查目標用戶的瀏覽器兼容性。
- **性能考慮**：過於複雜的動畫可能導致性能問題，特別是在滾動時。如果可能，簡化動畫以提高性能。
- **滾動容器**：確保正確設置滾動容器，因為錯誤的容器會導致動畫無法正確觸發。

## 總結
ScrollTimeline 是一個強大的 API，可幫助開發者創建基於滾動的動畫，提升網站的互動性和用戶體驗。