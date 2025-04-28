<!--
Meta Description: # SVGSVGElement：JavaScript 中的 SVG 根元素 ## 摘要 SVGSVGElement 是一個代表 SVG（可縮放矢量圖形）文檔的根元素的 JavaScript 介面。它使開發者能夠使用 JavaScript 操作和管理 SVG 圖形，實現動態的視覺效果。 ## 文檔 S...
Meta Keywords: svg, svgelement, setattribute, svgsvgelement, javascript
-->

# SVGSVGElement：JavaScript 中的 SVG 根元素

## 摘要
SVGSVGElement 是一個代表 SVG（可縮放矢量圖形）文檔的根元素的 JavaScript 介面。它使開發者能夠使用 JavaScript 操作和管理 SVG 圖形，實現動態的視覺效果。

## 文檔
SVGSVGElement 是所有 SVG 元素的容器，並且是 SVG 文檔的起始點。這個介面繼承自 Element，讓開發者能夠對 SVG 的屬性和方法進行操作。通過 SVGSVGElement，開發者可以創建、修改和刪除 SVG 圖形，並對其進行動畫處理。

### 主要屬性
- `width` 和 `height`：控制 SVG 的寬度和高度。
- `viewBox`：定義 SVG 的坐標系。
- `preserveAspectRatio`：控制 SVG 在不同顯示區域中的縮放方式。

### 主要方法
- `getElementById()`：通過 ID 獲取 SVG 內部的元素。
- `createElementNS()`：創建一個新的 SVG 元素。

### 用法
在 JavaScript 中，開發者可以通過 `document.createElementNS` 方法來創建一個 SVGSVGElement，並使用 `appendChild` 方法將其添加到 DOM 中。

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const svgElement = document.createElementNS(svgNamespace, "svg");
svgElement.setAttribute("width", "100");
svgElement.setAttribute("height", "100");
document.body.appendChild(svgElement);
```

## 範例
以下是使用 SVGSVGElement 的基本範例：

```javascript
// 創建 SVG 根元素
const svgNamespace = "http://www.w3.org/2000/svg";
const svgElement = document.createElementNS(svgNamespace, "svg");
svgElement.setAttribute("width", "200");
svgElement.setAttribute("height", "200");

// 創建一個圓形
const circle = document.createElementNS(svgNamespace, "circle");
circle.setAttribute("cx", "100");
circle.setAttribute("cy", "100");
circle.setAttribute("r", "50");
circle.setAttribute("fill", "red");

// 將圓形添加到 SVG 元素
svgElement.appendChild(circle);

// 將 SVG 元素添加到文檔中
document.body.appendChild(svgElement);
```

## 解釋
使用 SVGSVGElement 時，開發者需要注意以下幾點：
- 確保在創建 SVG 元素時使用正確的命名空間（namespace），否則可能無法正確顯示。
- 在操作 SVG 元素時，必須使用 SVG 專用的方法和屬性，像是 `setAttribute` 方法。

### 常見誤區
- 不要將 SVG 元素的創建與 HTML 元素混淆，必須使用 `createElementNS` 方法來確保正確的命名空間。
- 確保在 DOM 中添加 SVG 元素之前，已正確設置其屬性，這樣才能避免顯示問題。

## 一句總結
SVGSVGElement 是一個強大的 JavaScript 介面，可讓開發者創建和管理 SVG 圖形，實現動態和互動的視覺效果。