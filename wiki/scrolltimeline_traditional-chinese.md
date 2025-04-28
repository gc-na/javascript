<!--
Meta Description: # ScrollTimeline：JavaScript 中的滾動時間軸功能 ## 簡介 ScrollTimeline 是一個前端 Web API，旨在為網頁提供基於滾動事件的動畫效果，允許開發者根據用戶的滾動位置來驅動 CSS 動畫或 JavaScript 效果。 ## 文件說明 ### 目的 Sc...
Meta Keywords: scrolltimeline, javascript, css, const, timeline
-->

# ScrollTimeline：JavaScript 中的滾動時間軸功能

## 簡介
ScrollTimeline 是一個前端 Web API，旨在為網頁提供基於滾動事件的動畫效果，允許開發者根據用戶的滾動位置來驅動 CSS 動畫或 JavaScript 效果。

## 文件說明

### 目的
ScrollTimeline 旨在簡化基於滾動的動畫實現，提升用戶體驗。它提供了一種直觀的方式來將滾動位置映射到動畫進度，並能夠與 CSS 動畫和 JavaScript 效果無縫協作。

### 使用方式
ScrollTimeline 可以與 CSS 動畫搭配使用，通過定義一個新的時間軸來實現。使用者需要創建一個 ScrollTimeline 實例，然後將其應用到 CSS 動畫中。

#### 基本語法
```javascript
const timeline = new ScrollTimeline({
    scrollSource: document.querySelector('#scroll-container'),
    orientation: 'block', // 或 'inline'
    timeRange: 1000 // 滾動範圍
});
```

### 參數說明
- **scrollSource**：指定滾動容器的 DOM 元素。
- **orientation**：定義滾動的方向，支持 'block'（垂直）或 'inline'（水平）。
- **timeRange**：設定滾動範圍，通常是以像素為單位。

## 範例

### 基本使用範例
以下是一個簡單的使用範例，展示如何使用 ScrollTimeline 來控制元素的透明度隨著滾動而變化。

```html
<div id="scroll-container" style="height: 200vh;">
    <div id="animated-element" style="opacity: 0;">滾動以查看效果</div>
</div>

<style>
    #animated-element {
        transition: opacity 0.5s;
    }
</style>

<script>
    const scrollContainer = document.querySelector('#scroll-container');
    const animatedElement = document.querySelector('#animated-element');

    const timeline = new ScrollTimeline({
        scrollSource: scrollContainer,
        orientation: 'block',
        timeRange: 2000 // 2000 像素的滾動範圍
    });

    animatedElement.animate(
        [
            { opacity: 0 },
            { opacity: 1 }
        ],
        {
            timeline: timeline,
            duration: 1000 // 動畫持續時間
        }
    );
</script>
```

## 解釋
在使用 ScrollTimeline 時，開發者需注意以下幾點：
- 確保滾動容器的高度足夠，否則可能無法觸發滾動事件。
- 適當設定 timeRange，以確保動畫效果與滾動速度相匹配。
- 對於大範圍滾動，可能需要調整動畫的持續時間和效果，以避免用戶體驗不佳。

## 一句總結
ScrollTimeline 是一個強大的 API，讓開發者可以輕鬆根據用戶的滾動行為來控制動畫效果，提升網頁互動性和吸引力。