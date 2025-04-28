<!--
Meta Description: # DOMQuad：JavaScript 中的 DOM 物件 ## 概述 DOMQuad 是一個用於表示四邊形的物件，通常在處理 HTML 元素的邊界框和座標時使用。它是 `getClientRects()` 和 `getBoundingClientRect()` 方法的返回值，能夠提供元素在視口中...
Meta Keywords: domquad, getboundingclientrect, rect, javascript, html
-->

# DOMQuad：JavaScript 中的 DOM 物件

## 概述
DOMQuad 是一個用於表示四邊形的物件，通常在處理 HTML 元素的邊界框和座標時使用。它是 `getClientRects()` 和 `getBoundingClientRect()` 方法的返回值，能夠提供元素在視口中的位置和大小資訊。

## 文檔
### 目的
DOMQuad 物件主要用於獲取元素的大小和在視口中的位置，對於需要進行精確排版或碰撞檢測的應用場景非常有用。

### 使用方式
DOMQuad 物件包含了一組屬性，具體如下：
- `x` 和 `y`：代表四邊形的左上角坐標。
- `width` 和 `height`：代表四邊形的寬度和高度。
- `top` 和 `right`：代表四邊形的上邊和右邊的坐標。
- `bottom` 和 `left`：代表四邊形的下邊和左邊的坐標。

### 詳細信息
DOMQuad 物件可以通過以下方法獲取：

1. **getClientRects()**：該方法返回一組 DOMRect 物件，表示元素的所有邊界矩形。
2. **getBoundingClientRect()**：該方法返回一個 DOMRect 物件，表示元素的單一邊界矩形。

這些邊界矩形的坐標是相對於視口的，因此在處理滾動或不同顯示設備時特別有用。

## 範例
以下是使用 DOMQuad 的基本範例：

```javascript
// 獲取元素
const element = document.getElementById('myElement');

// 使用 getBoundingClientRect 獲取 DOMQuad 物件
const rect = element.getBoundingClientRect();

// 輸出矩形的坐標和大小
console.log(`左上角坐標: (${rect.left}, ${rect.top})`);
console.log(`寬度: ${rect.width}, 高度: ${rect.height}`);
```

## 解釋
在使用 DOMQuad 時，有幾個常見的陷阱和注意事項：
- **滾動條影響**：如果頁面有滾動條，`getBoundingClientRect()` 返回的坐標是相對於視口的，因此不會考慮滾動位置。
- **轉換效果**：在使用 CSS 轉換 (transform) 的元素上，返回的坐標可能會受到影響，導致計算出來的邊界矩形不準確。
- **顯示設備**：在不同的顯示設備上，特別是高解析度顯示器 (如 Retina 顯示屏)，需要注意坐標的精度。

## 一句總結
DOMQuad 是用於表示和獲取 HTML 元素在視口中的位置和大小的 JavaScript 物件。