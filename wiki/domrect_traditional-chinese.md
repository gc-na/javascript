<!--
Meta Description: # DOMRect：JavaScript 中的矩形物件 ## 摘要 DOMRect 物件提供了用於表示矩形範圍的屬性和方法，通常用於計算和操作 HTML 元素的尺寸及其在視窗中的位置。 ## 文檔 ### 目的 DOMRect 物件主要用於提供一組屬性來描述矩形的大小（寬度和高度）和位置（座標）。這...
Meta Keywords: domrect, rect, getboundingclientrect, const, javascript
-->

# DOMRect：JavaScript 中的矩形物件

## 摘要
DOMRect 物件提供了用於表示矩形範圍的屬性和方法，通常用於計算和操作 HTML 元素的尺寸及其在視窗中的位置。

## 文檔
### 目的
DOMRect 物件主要用於提供一組屬性來描述矩形的大小（寬度和高度）和位置（座標）。這在處理網頁元素的佈局和碰撞檢測時非常有用。

### 使用方式
DOMRect 可以通過多種方式獲得，最常見的是使用 `getBoundingClientRect()` 方法，該方法返回一個 DOMRect 物件，該物件描述了元素的大小和相對於視窗的位置信息。

### 屬性
DOMRect 物件包含以下屬性：
- `x`：矩形的左上角的 X 坐標。
- `y`：矩形的左上角的 Y 坐標。
- `width`：矩形的寬度。
- `height`：矩形的高度。
- `top`：矩形的上邊界的 Y 坐標。
- `right`：矩形的右邊界的 X 坐標。
- `bottom`：矩形的下邊界的 Y 坐標。
- `left`：矩形的左邊界的 X 坐標。

## 範例
### 基本用法
```javascript
// 獲取一個 DOM 元素
const element = document.getElementById('myElement');

// 使用 getBoundingClientRect 獲取 DOMRect
const rect = element.getBoundingClientRect();

// 輸出矩形的屬性
console.log(`X: ${rect.x}, Y: ${rect.y}, Width: ${rect.width}, Height: ${rect.height}`);
```

### 計算元素的相對位置
```javascript
const rect = document.querySelector('.myElement').getBoundingClientRect();
const isElementVisible = rect.top >= 0 && rect.bottom <= window.innerHeight;

console.log(`元素是否在視窗內: ${isElementVisible}`);
```

## 說明
在使用 DOMRect 時，開發者需注意以下幾點：
- `getBoundingClientRect()` 返回的數據是相對於視窗的，因此在頁面滾動時，值會隨之改變。
- 在某些情況下，DOMRect 的屬性可能會返回浮點數，這可能導致在進行大小或位置的比較時出現精度問題。
- 确保在元素完全加載後再調用 `getBoundingClientRect()`，否則可能獲取到不正確的數據。

## 一句總結
DOMRect 是一個用於表示矩形的物件，能夠有效地幫助開發者獲取和操作 HTML 元素的尺寸及其在視窗中的位置。