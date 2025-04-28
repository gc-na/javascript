<!--
Meta Description: # SVGRectElement：JavaScript 中的矩形元素 ## 概述 SVGRectElement 是一個用於創建和操作 SVG 矩形的 JavaScript 介面。它是 SVG（可縮放向量圖形）的一部分，可以在網頁中顯示和控制矩形形狀。 ## 文檔 SVGRectElement 代表 ...
Meta Keywords: svg, rect, setattribute, javascript, svgrectelement
-->

# SVGRectElement：JavaScript 中的矩形元素

## 概述
SVGRectElement 是一個用於創建和操作 SVG 矩形的 JavaScript 介面。它是 SVG（可縮放向量圖形）的一部分，可以在網頁中顯示和控制矩形形狀。

## 文檔
SVGRectElement 代表 SVG 中的矩形元素，允許開發者通過 JavaScript 來動態地創建和修改矩形。這些矩形可以透過屬性來定義其位置、大小和樣式，包括寬度、高度、圓角等。

### 主要屬性
- `x`：矩形左上角的 x 坐標。
- `y`：矩形左上角的 y 坐標。
- `width`：矩形的寬度。
- `height`：矩形的高度。
- `rx`：矩形的圓角半徑（水平）。
- `ry`：矩形的圓角半徑（垂直）。

### 使用方法
要使用 SVGRectElement，您通常需要先在 SVG 環境中創建一個矩形元素。然後可以通過 JavaScript 來訪問和修改其屬性。

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const rect = document.createElementNS(svgNamespace, "rect");

rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
rect.setAttribute("fill", "blue");

document.getElementById("svgContainer").appendChild(rect);
```

## 示例
以下是創建和修改 SVG 矩形的基本示例：

```javascript
// 創建 SVG 環境
const svgNamespace = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNamespace, "svg");
svg.setAttribute("width", 200);
svg.setAttribute("height", 200);
document.body.appendChild(svg);

// 創建一個矩形
const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", 50);
rect.setAttribute("y", 50);
rect.setAttribute("width", 100);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "red");

// 將矩形添加到 SVG 中
svg.appendChild(rect);

// 修改矩形的顏色
rect.setAttribute("fill", "green");
```

## 解釋
使用 SVGRectElement 時，有幾個常見的問題需要注意：

1. **命名空間**：必須使用 `createElementNS` 方法來創建 SVG 元素，因為 SVG 使用 XML 命名空間。
2. **屬性型別**：某些屬性需要以正確的數值型別設置（如整數或浮點數），否則可能無法正確顯示。
3. **樣式應用**：可以使用 CSS 來設置樣式，但某些屬性（如 `fill` 和 `stroke`）也可以直接在元素上設置。

## 一句總結
SVGRectElement 是 JavaScript 中用於創建和管理 SVG 矩形的強大工具。