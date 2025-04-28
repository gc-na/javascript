<!--
Meta Description: # PerformanceMark：JavaScript 性能標記的完整指南 ## 概述 PerformanceMark 是一個 JavaScript API，旨在幫助開發者在應用程序中記錄和測量性能指標，從而提升網站或應用程序的效能和用戶體驗。 ## 文檔 ### 目的 PerformanceMa...
Meta Keywords: performance, performancemark, javascript, mark, measure
-->

# PerformanceMark：JavaScript 性能標記的完整指南

## 概述
PerformanceMark 是一個 JavaScript API，旨在幫助開發者在應用程序中記錄和測量性能指標，從而提升網站或應用程序的效能和用戶體驗。

## 文檔
### 目的
PerformanceMark 允許開發者在關鍵事件發生時創建性能標記，這些標記可以在性能分析中使用，幫助識別瓶頸或性能問題。

### 使用方式
要使用 PerformanceMark，開發者可以使用 `performance.mark()` 方法來創建標記。該方法接受一個字符串作為標記的名稱，並可選擇提供一個字典對象作為選項。

#### 語法
```javascript
performance.mark(markName, options);
```

- **markName**: (String) 標記的名稱，這個名稱必須是唯一的。
- **options**: (Optional Object) 包含附加選項的對象，例如 `startTime` 和 `duration`。

### 詳細說明
- 標記可以用於測量從一個標記到另一個標記的時間間隔。
- 標記是可以在瀏覽器的性能條件下查看的，開發者可以使用 `performance.getEntriesByType('mark')` 來獲取所有標記的條目。
- 在創建標記後，這些標記會被存儲在 Performance Timeline 中，這樣開發者可以進行後續的性能分析。

## 示例
### 基本使用範例
以下是如何使用 PerformanceMark 創建一個標記的簡單範例：

```javascript
// 創建一個性能標記
performance.mark('start');

// 執行一些代碼
for (let i = 0; i < 1000000; i++) {
    // 模擬計算
}

// 創建另一個性能標記
performance.mark('end');

// 測量兩個標記之間的時間
performance.measure('my-measure', 'start', 'end');

// 獲取測量結果
const measures = performance.getEntriesByType('measure');
console.log(measures); // 輸出測量結果
```

## 解釋
### 常見問題
- **標記名稱重複**: 若使用相同的標記名稱，新的標記會覆蓋舊的標記，這可能導致數據丟失。
- **性能影響**: 雖然 PerformanceMark 自身對性能影響微乎其微，但過度使用可能會導致瀏覽器性能監控變得複雜。
- **未正確處理的測量**: 使用 `performance.measure()` 時，確保標記名稱存在，否則會導致錯誤。

### 附加說明
PerformanceMark 的使用為性能優化提供了一個強大的工具，開發者應根據具體需求合理設定標記，以便更好地分析和優化性能。

## 一句話總結
PerformanceMark 是一個用於記錄性能標記的 JavaScript API，能夠幫助開發者測量和分析應用程序性能。