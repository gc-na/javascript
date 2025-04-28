<!--
Meta Description: # SVGGeometryElement：JavaScript 中的 SVG 幾何元素 ## 概述 SVGGeometryElement 是一個用於表示 SVG（可縮放向量圖形）中幾何形狀的基礎接口，這些形狀包括圓形、矩形、多邊形等。它是 SVG 中的核心組件，與 JavaScript 一起使用時，...
Meta Keywords: svg, circle, svggeometryelement, setattribute, javascript
-->

# SVGGeometryElement：JavaScript 中的 SVG 幾何元素

## 概述
SVGGeometryElement 是一個用於表示 SVG（可縮放向量圖形）中幾何形狀的基礎接口，這些形狀包括圓形、矩形、多邊形等。它是 SVG 中的核心組件，與 JavaScript 一起使用時，可以讓開發者動態操控和修改圖形。

## 文檔
SVGGeometryElement 是所有 SVG 幾何形狀（例如 `<circle>`、`<rect>`、`<line>`、`<polygon>` 等）的基類。它提供了一些方法和屬性，可以用來獲取和設置形狀的各種屬性，如位置、大小和填充顏色。

### 目的
SVGGeometryElement 的主要目的是讓開發者在網頁上創建和操作圖形，提供更豐富的視覺效果和交互體驗。

### 使用方法
在 JavaScript 中，可以通過選擇 SVG 元素或創建新的 SVG 元素來獲取 SVGGeometryElement 的實例。以下是一些常見的使用方法：

- **選擇 SVG 元素**：使用 `document.querySelector()` 或 `getElementById()` 方法來獲取元素。
- **創建新元素**：使用 `document.createElementNS()` 方法來創建新的 SVG 幾何元素。

### 屬性和方法
- **屬性**：
  - `x`、`y`：元素的位置。
  - `width`、`height`：元素的大小。
  - `fill`、`stroke`：填充和邊框顏色。

- **方法**：
  - `getTotalLength()`：獲取路徑的總長度。
  - `getPointAtLength(length)`：根據長度獲取路徑上的點。

## 範例
以下是一些基本的使用範例：

### 創建一個圓形
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", 50);
circle.setAttribute("cy", 50);
circle.setAttribute("r", 40);
circle.setAttribute("fill", "red");
document.querySelector("svg").appendChild(circle);
```

### 獲取並修改矩形的屬性
```javascript
const rect = document.getElementById("myRect");
rect.setAttribute("width", 200);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "blue");
```

## 解釋
使用 SVGGeometryElement 時，開發者需注意以下幾點：

- **命名空間**：創建 SVG 元素時，必須使用正確的命名空間（`http://www.w3.org/2000/svg`）。
- **屬性值類型**：確保設置的屬性值類型正確，例如，`width` 和 `height` 必須是數字字符串。
- **不支持的屬性**：某些屬性可能不適用於所有幾何元素，使用前需確認其有效性。

## 一句總結
SVGGeometryElement 是 JavaScript 中用於創建和操作 SVG 幾何形狀的基礎接口，為開發者提供了強大的圖形處理能力。