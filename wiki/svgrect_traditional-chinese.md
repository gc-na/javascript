<!--
Meta Description: # SVGRect：JavaScript 中的矩形元素 ## 概述 SVGRect 是一個用於在 SVG（可縮放矢量圖形）中創建矩形的 JavaScript 物件。它提供了一個簡單的方式來定義矩形的大小、位置以及其他屬性，使開發者能夠在網頁上輕鬆地繪製和操作圖形。 ## 文檔 ### 目的 SVGR...
Meta Keywords: svg, rect, svgrect, javascript, setattribute
-->

# SVGRect：JavaScript 中的矩形元素

## 概述
SVGRect 是一個用於在 SVG（可縮放矢量圖形）中創建矩形的 JavaScript 物件。它提供了一個簡單的方式來定義矩形的大小、位置以及其他屬性，使開發者能夠在網頁上輕鬆地繪製和操作圖形。

## 文檔
### 目的
SVGRect 物件主要用於表示 SVG 中的矩形形狀。它的屬性和方法使得創建和操控矩形變得直觀且高效。

### 使用方式
在 JavaScript 中，SVGRect 通常與 SVG 元素一起使用。可以通過 `createElementNS` 方法創建一個矩形，並設置其屬性，例如 `x`、`y`、`width` 和 `height`。

#### 基本語法
```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let rect = document.createElementNS(svgNamespace, "rect");
```

### 屬性
- `x`：矩形左上角的 x 坐標。
- `y`：矩形左上角的 y 坐標。
- `width`：矩形的寬度。
- `height`：矩形的高度。
- `fill`：矩形的填充顏色。

### 方法
SVGRect 本身沒有特定的方法，但可以使用 DOM 操作來改變其屬性。

## 範例
### 基本範例
```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let svg = document.createElementNS(svgNamespace, "svg");
document.body.appendChild(svg);

let rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
rect.setAttribute("fill", "blue");

svg.appendChild(rect);
```

### 動態改變矩形顏色
```javascript
rect.addEventListener("click", function() {
    this.setAttribute("fill", "red");
});
```

## 解釋
在使用 SVGRect 時，開發者需要注意以下幾點：
- 確保使用正確的 SVG 名稱空間，否則無法正確創建矩形。
- 在設置屬性時，必須使用 `setAttribute` 方法，因為直接訪問屬性可能會導致錯誤。
- 確定矩形的坐標和大小，以避免它被畫布外的區域遮擋。

## 一句總結
SVGRect 是 JavaScript 中用於創建和操作 SVG 矩形的關鍵物件，為開發者提供了靈活的圖形繪製功能。