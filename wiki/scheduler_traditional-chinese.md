<!--
Meta Description: # JavaScript 調度器 (Scheduler) 詳細指南 ## 概要 JavaScript 調度器是一種用於管理和執行非同步任務的工具，幫助開發者有效地控制程式的執行時序，特別在處理大量事件或任務時。 ## 文檔 ### 目的 調度器的主要目的是在 JavaScript 的事件循環中，為不...
Meta Keywords: javascript, setinterval, console, log, requestanimationframe
-->

# JavaScript 調度器 (Scheduler) 詳細指南

## 概要
JavaScript 調度器是一種用於管理和執行非同步任務的工具，幫助開發者有效地控制程式的執行時序，特別在處理大量事件或任務時。

## 文檔
### 目的
調度器的主要目的是在 JavaScript 的事件循環中，為不同的任務分配執行優先權，確保系統的響應性和流暢性。

### 使用方式
調度器通常透過 `setTimeout`、`setInterval` 和 `requestAnimationFrame` 等方法來實現。這些方法可以將任務排入事件隊列，根據需求進行調度與執行。

### 詳細說明
- **setTimeout(callback, delay)**: 在指定的延遲時間後執行一次回調函數。
- **setInterval(callback, interval)**: 每隔指定的時間間隔重複執行回調函數。
- **requestAnimationFrame(callback)**: 提供一種在瀏覽器重繪之前執行任務的方式，適合用於動畫的調度。

這些方法能夠讓開發者更靈活地管理任務的執行時機，並幫助避免阻塞主執行緒。

## 範例
### 使用 setTimeout
```javascript
console.log("開始計時");
setTimeout(() => {
    console.log("計時結束");
}, 2000);
```

### 使用 setInterval
```javascript
let count = 0;
const intervalId = setInterval(() => {
    count++;
    console.log(`計數: ${count}`);
    if (count === 5) {
        clearInterval(intervalId);
        console.log("計時結束");
    }
}, 1000);
```

### 使用 requestAnimationFrame
```javascript
let start = null;

function animate(timestamp) {
    if (!start) start = timestamp;
    const progress = timestamp - start;
    console.log(`動畫進行中: ${progress} 毫秒`);
    
    if (progress < 2000) { // 持續兩秒
        requestAnimationFrame(animate);
    } else {
        console.log("動畫結束");
    }
}

requestAnimationFrame(animate);
```

## 解釋
在使用調度器時，開發者需注意以下幾點：
1. **非同步執行**: 調度器中的任務是非同步執行的，可能會導致任務執行的順序與預期不同。
2. **性能影響**: 過多的定時任務會影響應用的性能，特別是在使用 `setInterval` 時。
3. **清理工作**: 使用 `setInterval` 時，務必在適當的時候使用 `clearInterval` 來避免內存洩漏。

## 總結
JavaScript 調度器是一種強大的工具，幫助開發者有效處理非同步任務，提升應用的性能與用戶體驗。