<!--
Meta Description: # PerformancePaintTiming：JavaScript 性能指標的深入解析 ## 概述 PerformancePaintTiming 是一種 JavaScript API，旨在提供關於頁面繪製性能的詳細資訊。這個指標可以幫助開發者了解何時開始和結束首次繪製，以及在渲染過程中出現的性能...
Meta Keywords: performancepainttiming, api, javascript, performance, getentriesbytype
-->

# PerformancePaintTiming：JavaScript 性能指標的深入解析

## 概述
PerformancePaintTiming 是一種 JavaScript API，旨在提供關於頁面繪製性能的詳細資訊。這個指標可以幫助開發者了解何時開始和結束首次繪製，以及在渲染過程中出現的性能瓶頸。

## 文檔
### 目的
PerformancePaintTiming API 是一個用於測量和分析頁面構建過程中重繪的性能工具。它特別關注「首次有效繪製」（FCP）和「首次內容繪製」（FMP），這些指標對於提升用戶體驗至關重要。

### 使用方式
要使用 PerformancePaintTiming，開發者可以通過 `performance.getEntriesByType('paint')` 方法來獲取所有的繪製事件。這些事件會返回一個包含重要繪製時間的陣列。

### 詳細說明
- **首次有效繪製（FCP）**：指從頁面開始載入到瀏覽器首次繪製任何可見內容的時間。
- **首次內容繪製（FMP）**：指從頁面開始載入到瀏覽器首次繪製主要內容的時間。

這些時間是網頁性能優化中的關鍵指標，能夠幫助開發者識別潛在的性能問題。

## 範例
### 基本使用範例
```javascript
// 獲取繪製時間條目
const paintEntries = performance.getEntriesByType('paint');

// 輸出首次有效繪製時間
paintEntries.forEach(entry => {
    console.log(`${entry.name}: ${entry.startTime}毫秒`);
});
```

## 解釋
### 常見問題
- **支持性問題**：並非所有瀏覽器都支持 PerformancePaintTiming API，開發者應該檢查瀏覽器的兼容性。
- **性能測量**：在某些情況下，測量結果可能因網絡延遲或其他資源加載問題而有所偏差，因此建議多次測試並取平均值。

### 注意事項
- 確保在頁面完全載入後再調用 `performance.getEntriesByType('paint')`，以獲得準確的數據。
- 使用此 API 時，請注意隱私和性能的平衡，避免過度追蹤可能影響用戶體驗。

## 一句總結
PerformancePaintTiming API 提供關於頁面繪製性能的關鍵指標，有助於開發者優化用戶體驗。