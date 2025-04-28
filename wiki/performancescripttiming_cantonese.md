<!--
Meta Description: # PerformanceScriptTiming：提升JavaScript效能的關鍵指標 ## 概述 PerformanceScriptTiming 是一個 JavaScript API 的一部分，旨在幫助開發者衡量和分析網頁中腳本的性能。透過這個 API，開發者可以獲取有關腳本執行時間的詳細數據...
Meta Keywords: script, performancescripttiming, console, log, javascript
-->

# PerformanceScriptTiming：提升JavaScript效能的關鍵指標

## 概述
PerformanceScriptTiming 是一個 JavaScript API 的一部分，旨在幫助開發者衡量和分析網頁中腳本的性能。透過這個 API，開發者可以獲取有關腳本執行時間的詳細數據，從而優化網頁的加載速度和用戶體驗。

## 文檔
PerformanceScriptTiming 主要用於收集有關 JavaScript 腳本的性能數據。它提供了以下幾個重要屬性：

- **startTime**: 腳本開始執行的時間（以毫秒為單位）。
- **endTime**: 腳本結束執行的時間（以毫秒為單位）。
- **duration**: 腳本執行的總時間，這是 endTime 和 startTime 的差值。
- **name**: 腳本的名稱或 URL，用於識別特定的腳本。

這些數據可以幫助開發者分析不同腳本的性能，並針對性地進行優化。

### 使用方法
在使用 PerformanceScriptTiming 之前，確保你的環境支持 Performance API。你可以通過以下方式訪問性能數據：

```javascript
// 獲取所有腳本的性能數據
const scripts = performance.getEntriesByType("script");
scripts.forEach(script => {
    console.log(`腳本名稱: ${script.name}`);
    console.log(`開始時間: ${script.startTime} ms`);
    console.log(`結束時間: ${script.endTime} ms`);
    console.log(`執行時間: ${script.duration} ms`);
});
```

## 範例
以下是一個簡單的使用範例，展示如何使用 PerformanceScriptTiming 獲取腳本性能數據：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>PerformanceScriptTiming 示例</title>
</head>
<body>
    <script src="example.js"></script>
    <script>
        // 獲取性能數據
        const scripts = performance.getEntriesByType("script");
        scripts.forEach(script => {
            console.log(`腳本名稱: ${script.name}`);
            console.log(`執行時間: ${script.duration} ms`);
        });
    </script>
</body>
</html>
```

## 解釋
在使用 PerformanceScriptTiming 時，有幾個常見的注意事項：

1. **瀏覽器支持**: 確保目標用戶的瀏覽器支持 Performance API，否則可能無法獲取正確的性能數據。
2. **異步腳本**: 對於使用 `async` 或 `defer` 加載的腳本，性能數據可能會有所不同，因此在分析時需要特別注意。
3. **數據量**: 當加載大量腳本時，性能數據可能會變得複雜，因此建議針對特定腳本進行分析，以獲得更清晰的結果。

## 一句總結
PerformanceScriptTiming 是一個有助於開發者分析和優化 JavaScript 腳本性能的重要工具。