<!--
Meta Description: # TextMetrics：JavaScript 中的文本度量工具 ## 概要 TextMetrics 是一個用於測量文本大小和特徵的 JavaScript 對象。它提供了一系列屬性，幫助開發者了解文本在畫布或其他渲染上下文中的顯示效果，從而實現更精確的排版和設計。 ## 文檔 ### 目的 Tex...
Meta Keywords: textmetrics, canvas, javascript, const, metrics
-->

# TextMetrics：JavaScript 中的文本度量工具

## 概要
TextMetrics 是一個用於測量文本大小和特徵的 JavaScript 對象。它提供了一系列屬性，幫助開發者了解文本在畫布或其他渲染上下文中的顯示效果，從而實現更精確的排版和設計。

## 文檔
### 目的
TextMetrics 的主要目的是提供文本的度量資訊，例如文本的寬度和高度，以便在繪製文本時能夠精確控制其位置和呈現方式。

### 用法
TextMetrics 主要通過 Canvas API 的 `measureText()` 方法來獲取。當你在 Canvas 上繪製文本時，可以使用此方法來獲得 TextMetrics 對象，然後從中提取文本的相關數據。

### 詳細說明
- **屬性**：
  - `width`: 返回所測量文本的寬度。
  - `actualBoundingBoxAscent`: 返回文本的實際邊界框上緣的高度（在字體呈現時的視覺效果）。
  - `actualBoundingBoxDescent`: 返回文本的實際邊界框下緣的深度。
  - `emHeightAscent`: 返回字母“m”所代表的字體高度的上緣。
  - `emHeightDescent`: 返回字母“m”所代表的字體高度的下緣。
  - `hangingBaseline`: 返回懸掛基線的高度。
  - `alphabeticBaseline`: 返回字母基線的高度。

### 示例
```javascript
// 創建一個 Canvas 元素
const canvas = document.createElement('canvas');
const ctx = canvas.getContext('2d');

// 設定字體樣式
ctx.font = '16px Arial';

// 測量文本
const text = 'Hello, World!';
const metrics = ctx.measureText(text);

// 獲取文本度量資訊
console.log('文本寬度:', metrics.width);
console.log('實際邊界框上緣:', metrics.actualBoundingBoxAscent);
console.log('實際邊界框下緣:', metrics.actualBoundingBoxDescent);
```

## 解釋
在使用 TextMetrics 時，開發者需要注意以下幾點：
- **字體樣式**：測量結果會受到字體樣式的影響，因此在調用 `measureText()` 前必須正確設置上下文的字體。
- **畫布大小**：確保畫布的大小足夠顯示所有文本，否則可能無法正確獲取度量資訊。
- **不同字體的差異**：不同字體的測量結果可能會有所不同，因此在設計時需考慮到字體的選擇。

## 一句總結
TextMetrics 是一個強大的工具，可以幫助開發者精確測量文本在 JavaScript 中的顯示特性。