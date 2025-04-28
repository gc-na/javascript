<!--
Meta Description: # PerformanceResourceTiming 在 JavaScript 中的應用 ## 概要 PerformanceResourceTiming 是一個 JavaScript API，專門用於收集和分析網絡資源的性能數據，以幫助開發人員優化網頁加載速度和提升用戶體驗。 ## 文檔 ### ...
Meta Keywords: performanceresourcetiming, entry, performance, console, log
-->

# PerformanceResourceTiming 在 JavaScript 中的應用

## 概要
PerformanceResourceTiming 是一個 JavaScript API，專門用於收集和分析網絡資源的性能數據，以幫助開發人員優化網頁加載速度和提升用戶體驗。

## 文檔
### 目的
PerformanceResourceTiming 接口提供了關於加載網絡資源的詳細性能信息，包括請求開始時間、響應結束時間、以及各個階段的持續時間等，幫助開發者識別性能瓶頸。

### 使用方法
PerformanceResourceTiming 是 Performance API 的一部分，可以通過 `performance.getEntriesByType("resource")` 方法獲取資源的性能信息。這些信息是以 PerformanceResourceTiming 對象的形式返回的。

#### 主要屬性：
- `name`: 資源的 URL。
- `startTime`: 請求開始的時間戳。
- `duration`: 請求所花費的總時間。
- `fetchStart`: 開始發起請求的時間。
- `responseEnd`: 收到響應的時間。

### 範例
以下是使用 PerformanceResourceTiming 的基本範例：

```javascript
// 獲取所有資源的性能數據
const resourceEntries = performance.getEntriesByType("resource");

// 遍歷並輸出資源的性能信息
resourceEntries.forEach((entry) => {
    console.log(`資源: ${entry.name}`);
    console.log(`開始時間: ${entry.startTime} ms`);
    console.log(`持續時間: ${entry.duration} ms`);
    console.log(`響應結束時間: ${entry.responseEnd} ms`);
});
```

## 解釋
### 常見問題
- **數據不完整**: 在某些情況下，如果資源被快取，則 PerformanceResourceTiming 可能不返回完整的性能數據。
- **跨域問題**: 如果資源來自不同的域，某些屬性可能會受到 CORS（跨來源資源共享）限制，導致無法訪問。

### 附加提示
- 確保在文檔加載完成後再調用 `performance.getEntriesByType`，以獲得完整的資源數據。
- 考慮使用 PerformanceObserver 監控資源加載的性能數據，以便即時獲取性能指標。

## 一句總結
PerformanceResourceTiming 是一個強大的工具，幫助開發者分析和優化網頁資源的加載性能。