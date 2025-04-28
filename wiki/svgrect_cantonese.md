<!--
Meta Description: # SVGRect：JavaScript 中的矩形元素 ## 簡介 SVGRect 是一個在 JavaScript 中用於操作 SVG (可縮放矢量圖形) 矩形元素的接口。它提供了一系列的方法和屬性，讓開發者可以輕鬆地創建和修改 SVG 矩形。 ## 文件說明 SVGRect 主要用於定義和操作 S...
Meta Keywords: svg, rect, svgrect, setattribute, javascript
-->

# SVGRect：JavaScript 中的矩形元素

## 簡介
SVGRect 是一個在 JavaScript 中用於操作 SVG (可縮放矢量圖形) 矩形元素的接口。它提供了一系列的方法和屬性，讓開發者可以輕鬆地創建和修改 SVG 矩形。

## 文件說明
SVGRect 主要用於定義和操作 SVG 矩形的形狀和大小。這些矩形可以用於各種圖形應用，包括圖表、圖示和版面設計。SVGRect 的屬性包含 x、y、寬度和高度，這些屬性可以直接影響矩形的外觀。

### 目的
SVGRect 的主要目的是提供一種簡單的方式來創建和操作 SVG 矩形，並使其在 Web 應用中更具可視化。

### 用法
要使用 SVGRect，通常需要首先創建一個 SVG 元素，然後使用 JavaScript 來創建和操作矩形。以下是一些常用的屬性：
- `x`：矩形左上角的 x 座標。
- `y`：矩形左上角的 y 座標。
- `width`：矩形的寬度。
- `height`：矩形的高度。

## 範例
以下是一些基本的範例，展示如何使用 SVGRect：

### 創建一個簡單的 SVG 矩形
```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const rect = document.createElementNS(svgNS, "rect");

rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
rect.setAttribute("fill", "blue");

document.querySelector("svg").appendChild(rect);
```

### 修改矩形屬性
```javascript
rect.setAttribute("width", 150);
rect.setAttribute("height", 75);
rect.setAttribute("fill", "red");
```

## 解釋
在使用 SVGRect 時，開發者應該注意以下幾點：
- 確保 SVG 元素已經被正確創建，否則可能會導致錯誤。
- 使用 `createElementNS` 方法來創建 SVG 元素，因為這是 SVG 的命名空間。
- 當修改矩形屬性時，可能需要檢查其他樣式可能會影響最終顯示。

## 總結
SVGRect 是一個強大的工具，可以用於創建和操作 SVG 矩形，使其在 JavaScript 中的圖形處理變得更加簡單和高效。