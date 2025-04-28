<!--
Meta Description: # SVGLineElement 在 JavaScript 中的應用 ## 簡介 SVGLineElement 是一個用於創建和操作 SVG 中線條的 JavaScript 接口，允許開發者精確地控制線條的屬性和行為。 ## 文檔 SVGLineElement 是 SVG 中用來表示一條線的元素。它...
Meta Keywords: svg, line, stroke, svglineelement, width
-->

# SVGLineElement 在 JavaScript 中的應用

## 簡介
SVGLineElement 是一個用於創建和操作 SVG 中線條的 JavaScript 接口，允許開發者精確地控制線條的屬性和行為。

## 文檔
SVGLineElement 是 SVG 中用來表示一條線的元素。它的主要目的是在圖形中繪製直線，並提供了一系列屬性來設置線條的起點、終點、顏色、寬度等。

### 主要屬性：
- **x1**: 線的起點 X 坐標。
- **y1**: 線的起點 Y 坐標。
- **x2**: 線的終點 X 坐標。
- **y2**: 線的終點 Y 坐標。
- **stroke**: 線的顏色。
- **stroke-width**: 線的寬度。

### 使用方法
在 HTML 文件中，您可以通過 SVG 標籤創建 SVGLineElement。例如：

```html
<svg width="200" height="200">
  <line x1="10" y1="10" x2="100" y2="100" stroke="black" stroke-width="2" />
</svg>
```

在 JavaScript 中，您可以通過 `document.createElementNS` 方法創建一個 SVGLineElement：

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const line = document.createElementNS(svgNamespace, "line");

line.setAttribute("x1", "10");
line.setAttribute("y1", "10");
line.setAttribute("x2", "100");
line.setAttribute("y2", "100");
line.setAttribute("stroke", "black");
line.setAttribute("stroke-width", "2");

document.querySelector("svg").appendChild(line);
```

## 示例
以下是一個顯示 SVGLineElement 繪製線條的簡單示例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>SVGLineElement 示例</title>
</head>
<body>
    <svg width="200" height="200">
        <line x1="20" y1="20" x2="180" y2="20" stroke="red" stroke-width="4" />
        <line x1="20" y1="40" x2="180" y2="120" stroke="green" stroke-width="4" />
    </svg>
</body>
</html>
```

## 解釋
在使用 SVGLineElement 時，有幾個常見的陷阱需要注意：
- 確保 `x1`, `y1`, `x2`, `y2` 的值在 SVG 的寬度和高度範圍內，否則線條可能不會顯示。
- 線條的顏色和寬度必須正確設置，以確保在不同的背景上可見。
- 如果您在 JavaScript 中動態創建線條，請確保正確使用 SVG 命名空間。

## 簡單總結
SVGLineElement 是用於在 SVG 中繪製和控制線條的 JavaScript 接口，具有多種可定制的屬性。