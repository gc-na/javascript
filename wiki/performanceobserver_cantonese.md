<!--
Meta Description: # PerformanceObserver 在 JavaScript 中的應用 ## 簡介 PerformanceObserver 是一個強大的 JavaScript API，用於監控性能事件。它可以幫助開發者收集和分析 Web 應用程式的性能數據，以便進行優化。 ## 文檔 ### 目的 Perf...
Meta Keywords: performanceobserver, mark, entry, javascript, observer
-->

# PerformanceObserver 在 JavaScript 中的應用

## 簡介
PerformanceObserver 是一個強大的 JavaScript API，用於監控性能事件。它可以幫助開發者收集和分析 Web 應用程式的性能數據，以便進行優化。

## 文檔

### 目的
PerformanceObserver 主要用於觀察和記錄性能相關的事件，這些事件包括資源加載時間、DOM 渲染時間等。它提供了一種高效的方式來收集性能數據，並且不會對主線程造成太大的影響。

### 使用方法
要使用 PerformanceObserver，開發者需要創建一個 PerformanceObserver 實例並傳遞一個回調函數。這個回調函數會在觀察到指定的性能事件時被調用。以下是基本的語法：

```javascript
const observer = new PerformanceObserver((list) => {
    // 處理性能數據
    list.getEntries().forEach((entry) => {
        console.log(entry);
    });
});

// 開始觀察特定的性能事件
observer.observe({ entryTypes: ['measure', 'mark'] });
```

### 參數
- **entryTypes**: 一個字符串數組，指定要觀察的事件類型。目前支持的事件類型包括：`'mark'`、`'measure'` 和 `'resource'` 等。

## 範例

以下是如何使用 PerformanceObserver 監控性能事件的基本範例：

```javascript
// 創建一個 PerformanceObserver 實例
const observer = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`名稱: ${entry.name}, 持續時間: ${entry.duration}`);
    });
});

// 開始觀察 mark 事件
observer.observe({ entryTypes: ['mark'] });

// 設置一個 mark
performance.mark('start');

// 模擬一些延遲
setTimeout(() => {
    performance.mark('end');
    performance.measure('測量', 'start', 'end');
}, 1000);
```

## 解釋

### 常見問題
1. **性能數據的收集延遲**: PerformanceObserver 在某些情況下可能會延遲性能數據的收集，這可能會影響到即時監控的需求。
   
2. **觀察範圍的限制**: PerformanceObserver 只能觀察在其觀察範圍內的性能事件，若事件在觀察開始之前已經發生，則無法捕獲。

3. **性能影響**: 雖然 PerformanceObserver 設計上不會對性能造成太大影響，但過度使用可能仍會影響應用的效能，應謹慎使用。

## 一句總結
PerformanceObserver 是一個強大的工具，可以有效地監控和分析 Web 應用的性能數據，幫助開發者進行優化。