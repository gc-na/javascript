<!--
Meta Description: # PerformanceMark: JavaScript 性能標記的應用 ## 簡介 PerformanceMark 是一個 JavaScript API，用於在性能測試中創建和管理性能標記，幫助開發者測量和分析應用程序性能。 ## 文檔 ### 目的 PerformanceMark API 旨在...
Meta Keywords: performancemark, performance, mark, javascript, api
-->

# PerformanceMark: JavaScript 性能標記的應用

## 簡介
PerformanceMark 是一個 JavaScript API，用於在性能測試中創建和管理性能標記，幫助開發者測量和分析應用程序性能。

## 文檔
### 目的
PerformanceMark API 旨在提供一種簡單的方法來標記特定的性能事件，這些事件可以用於分析應用程序的性能瓶頸。這些標記可用於後續的性能測量和報告。

### 使用方法
要使用 PerformanceMark，開發者需要調用 `performance.mark()` 方法，並為其提供一個字符串參數，這個字符串將作為標記的名稱。以下是基本語法：

```javascript
performance.mark('markName');
```

一旦創建了標記，開發者可以使用 `performance.getEntriesByType('mark')` 方法來檢索所有標記，並進一步分析它們。

### 詳細說明
- **性能標記的特性**：
  - 標記是非持久性的，意味著它們在記憶體中存儲，直到被檢索或用於分析。
  - 標記的名稱應該是唯一的，以避免混淆。
  
- **性能測量的整合**：
  PerformanceMark 可以與其他性能測量 API（如 PerformanceMeasure 和 PerformanceObserver）結合使用，以獲取更全面的性能數據。

## 範例
以下是 PerformanceMark 的基本使用例子：

```javascript
// 創建一個性能標記
performance.mark('startTask');

// 執行某些任務
doSomeTask();

// 在任務完成後創建另一個標記
performance.mark('endTask');

// 獲取所有標記
const marks = performance.getEntriesByType('mark');
console.log(marks);
```

在這個例子中，我們創建了兩個標記，分別標記任務的開始和結束，然後檢索所有的標記並輸出到控制台。

## 解釋
### 常見問題
- **標記名稱衝突**：確保每個標記名稱都是唯一的，以避免在分析時產生混淆。
- **性能影響**：雖然 PerformanceMark 本身的性能開銷很小，但過多的標記可能會影響性能分析的準確性。

### 附註
- PerformanceMark 是一個相對簡單的 API，但在性能敏感的應用中，它的使用能夠顯著提升性能分析的精度。
- 確保在適當的時間點創建標記，以捕捉準確的性能數據。

## 總結
PerformanceMark 是一個強大的工具，能夠幫助開發者在 JavaScript 應用程序中有效地標記和分析性能事件。