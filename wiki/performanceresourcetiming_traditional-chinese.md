<!--
Meta Description: # PerformanceResourceTiming：JavaScript性能資源計時的深入解析 ## 概要 `PerformanceResourceTiming` 是一個Web API，提供有關資源加載性能的詳細信息，幫助開發者分析和優化網頁性能。 ## 文檔 ### 目的 `Performan...
Meta Keywords: resource, performanceresourcetiming, performance, getentriesbytype, duration
-->

# PerformanceResourceTiming：JavaScript性能資源計時的深入解析

## 概要
`PerformanceResourceTiming` 是一個Web API，提供有關資源加載性能的詳細信息，幫助開發者分析和優化網頁性能。

## 文檔
### 目的
`PerformanceResourceTiming` 主要用於獲取網頁資源（如圖片、腳本、樣式表等）加載的性能數據。這些數據可以幫助開發者識別加載瓶頸，提升用戶體驗。

### 使用方式
`PerformanceResourceTiming` 物件通過 `performance.getEntriesByType("resource")` 方法獲取，該方法返回一個包含所有資源加載性能數據的陣列。每個 `PerformanceResourceTiming` 物件包含多個屬性，例如：

- `startTime`：資源請求開始的時間。
- `duration`：資源加載的持續時間。
- `fetchStart`：資源請求開始的時間。
- `responseEnd`：資源響應結束的時間。
- `transferSize`：傳輸的字節數。

### 詳細信息
使用 `PerformanceResourceTiming` 之前，確保您的網頁在支持的瀏覽器中運行。這個API在現代瀏覽器中廣泛支持。可以通過以下代碼片段獲取並顯示網頁資源的性能數據：

```javascript
const resources = performance.getEntriesByType("resource");
resources.forEach((resource) => {
    console.log(`資源: ${resource.name}`);
    console.log(`加載時間: ${resource.duration} 毫秒`);
});
```

## 範例
以下是幾個基本用法的範例：

1. **獲取所有資源的性能數據**：

```javascript
const resources = performance.getEntriesByType("resource");
resources.forEach(resource => {
    console.log(`資源: ${resource.name}, 加載時間: ${resource.duration}`);
});
```

2. **篩選特定資源類型**：

```javascript
const scriptResources = performance.getEntriesByType("resource").filter(resource => resource.initiatorType === "script");
scriptResources.forEach(script => {
    console.log(`腳本: ${script.name}, 加載時間: ${script.duration}`);
});
```

## 解釋
### 常見陷阱
- **舊版瀏覽器支持**：部分舊版瀏覽器不支持 `PerformanceResourceTiming`，在使用前應檢查兼容性。
- **數據延遲**：在某些情況下，獲取的性能數據可能會有延遲，特別是在使用 `window.onload` 或其他事件時，這可能導致未完整收集數據。
- **資源過多**：如果網頁資源較多，數據分析可能會變得繁雜，建議對性能數據進行適當的篩選和整理。

## 總結
`PerformanceResourceTiming` 是一個強大的工具，幫助開發者監控和優化網頁資源的加載性能，從而提升整體用戶體驗。