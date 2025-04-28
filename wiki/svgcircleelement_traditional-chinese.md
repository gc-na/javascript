<!--
Meta Description: # SVGCircleElement：JavaScript 中的 SVG 圓形元素 ## 概述 SVGCircleElement 是一個代表 SVG 圓形的元素，允許開發者在網頁上使用 JavaScript 創建和操作圓形圖形。這個元素屬於 SVG（可縮放向量圖形）中，用於繪製圓形，並提供多種屬性來...
Meta Keywords: circle, svg, svgcircleelement, javascript, setattribute
-->

# SVGCircleElement：JavaScript 中的 SVG 圓形元素

## 概述
SVGCircleElement 是一個代表 SVG 圓形的元素，允許開發者在網頁上使用 JavaScript 創建和操作圓形圖形。這個元素屬於 SVG（可縮放向量圖形）中，用於繪製圓形，並提供多種屬性來調整其外觀和行為。

## 文檔
### 目的
SVGCircleElement 提供一種便捷的方式來在 SVG 中定義圓形，並可以通過 JavaScript 進行動態操作。這使得 SVG 圓形可以根據用戶輸入或其他事件進行交互和變化。

### 使用方法
SVGCircleElement 可以通過 Document.createElementNS() 方法創建，並且支援以下主要屬性：
- `cx`：圓心的 x 坐標。
- `cy`：圓心的 y 坐標。
- `r`：圓的半徑。
- `fill`：填充顏色。
- `stroke`：邊框顏色。
- `stroke-width`：邊框寬度。

### 詳細說明
以下是 SVGCircleElement 的基本結構：
```html
<svg width="200" height="200">
    <circle cx="100" cy="100" r="80" fill="red" />
</svg>
```

在 JavaScript 中，您可以這樣創建和操作一個圓形：
```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", 50);
circle.setAttribute("cy", 50);
circle.setAttribute("r", 40);
circle.setAttribute("fill", "blue");

document.querySelector("svg").appendChild(circle);
```

## 範例
以下是使用 SVGCircleElement 的基本範例：

### 創建一個紅色圓形
```html
<svg width="200" height="200">
    <circle cx="100" cy="100" r="50" fill="red" />
</svg>
```

### 使用 JavaScript 動態創建圓形
```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", 100);
circle.setAttribute("cy", 100);
circle.setAttribute("r", 60);
circle.setAttribute("fill", "green");
document.querySelector("svg").appendChild(circle);
```

## 解釋
在使用 SVGCircleElement 時，開發者需要注意以下幾點：
- 確保正確使用命名空間（`http://www.w3.org/2000/svg`），否則將無法正確創建圓形元素。
- 在設置屬性時，請確認數值的正確性，例如 cx、cy 和 r 必須是非負數。
- 在某些情況下，圓形可能會被其他元素遮擋或無法正常顯示，這需要調整其層級或位置。

## 單句總結
SVGCircleElement 是一個強大的工具，允許開發者在 JavaScript 中靈活地創建和操作 SVG 圓形元素。