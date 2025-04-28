<!--
Meta Description: # PerformanceServerTiming：JavaScript 性能測試的關鍵工具 ## 概述 PerformanceServerTiming 是一個用於測量伺服器響應性能的 JavaScript API，可以提供有關伺服器端操作的詳細時間資訊，幫助開發者優化應用程式性能。 ## 文件說明...
Meta Keywords: timing, performanceservertiming, javascript, server, http
-->

# PerformanceServerTiming：JavaScript 性能測試的關鍵工具

## 概述
PerformanceServerTiming 是一個用於測量伺服器響應性能的 JavaScript API，可以提供有關伺服器端操作的詳細時間資訊，幫助開發者優化應用程式性能。

## 文件說明
PerformanceServerTiming 是 Performance API 的一部分，允許開發者記錄伺服器響應的時間指標。這些指標可以在瀏覽器的開發者工具中查看，幫助開發者分析和改善網頁的載入時間與用戶體驗。

### 目的
PerformanceServerTiming 的主要目的是提供伺服器端性能數據，幫助開發者了解伺服器響應的各個階段所花費的時間。

### 使用方法
使用 PerformanceServerTiming 非常簡單，開發者可以在伺服器的 HTTP 響應標頭中添加 `Server-Timing` 標頭，並提供一系列的計時指標。這些指標可以包括伺服器處理請求的時間、數據庫查詢時間等。

### 詳細說明
1. **添加 Server-Timing 標頭**：
   ```http
   Server-Timing: db;dur=53, cache;desc="Cache Read";dur=47
   ```

2. **在 JavaScript 中讀取 PerformanceServerTiming 數據**：
   ```javascript
   const serverTimings = performance.getEntriesByType('navigation')[0].serverTiming;
   console.log(serverTimings);
   ```

這樣，開發者可以獲取和分析伺服器響應時間的各個指標。

## 範例
以下是使用 PerformanceServerTiming 的基本範例：

### 伺服器端設定
在伺服器端添加 `Server-Timing` 標頭：
```http
HTTP/1.1 200 OK
Server-Timing: db;dur=100, cache;dur=50
Content-Type: application/json
```

### 客戶端 JavaScript 代碼
在客戶端獲取伺服器性能數據：
```javascript
window.onload = function() {
   const navigationPerformance = performance.getEntriesByType('navigation')[0];
   if (navigationPerformance) {
       const timings = navigationPerformance.serverTiming;
       timings.forEach(timing => {
           console.log(`${timing.name}: ${timing.duration}ms`);
       });
   }
};
```

## 解釋
- **常見陷阱**：開發者可能會忘記在伺服器響應中添加 `Server-Timing` 標頭，這樣則無法獲取任何性能數據。
- **注意事項**：確保提供的計時指標名稱是唯一的，以避免數據混淆。此外，過多的計時指標會使數據過於冗雜，應當根據實際需要進行合理的設置。

## 一句總結
PerformanceServerTiming 是一個強大的 JavaScript 工具，用於測量和分析伺服器性能，助力開發者優化應用程式的響應時間。