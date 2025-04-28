<!--
Meta Description: # SVGLinearGradientElement：JavaScript中的SVG线性渐变元素 ## 简介 `SVGLinearGradientElement` 是一个在JavaScript中用于创建和操作SVG线性渐变的接口。它允许开发者定义渐变的起始和结束颜色，以及渐变的方向，广泛应用于图形绘...
Meta Keywords: setattribute, lineargradient, svglineargradientelement, svg, createelementns
-->

# SVGLinearGradientElement：JavaScript中的SVG线性渐变元素

## 简介
`SVGLinearGradientElement` 是一个在JavaScript中用于创建和操作SVG线性渐变的接口。它允许开发者定义渐变的起始和结束颜色，以及渐变的方向，广泛应用于图形绘制和图像效果。

## 文档
`SVGLinearGradientElement` 是SVG（可缩放矢量图形）规范的一部分，主要用于在图形元素上创建线性渐变效果。它提供了一种简单的方法来定义从一个颜色到另一个颜色的渐变过渡。

### 目的
`SVGLinearGradientElement` 主要用于：
- 为SVG图形元素添加颜色渐变效果。
- 提高图形的视觉吸引力。

### 使用
在JavaScript中，使用 `createElementNS` 方法可以创建 `SVGLinearGradientElement` 实例。它通常与 `<defs>` 标签结合使用，以便在SVG中重用渐变。

### 详细说明
- **属性**：
  - `x1`, `y1`, `x2`, `y2`：定义渐变的起始和结束坐标。
  - `gradientUnits`：指定坐标系统（如用户空间或对象空间）。
  - `spreadMethod`：定义渐变的扩展方式（如 `pad`, `reflect`, `repeat`）。
  
- **方法**：
  - `addColorStop(offset, color)`：在渐变中添加颜色停止点。

### 示例
以下是使用 `SVGLinearGradientElement` 创建线性渐变的基本示例：

```javascript
// 创建SVG元素
const svgNS = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNS, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");

// 创建线性渐变元素
const linearGradient = document.createElementNS(svgNS, "linearGradient");
linearGradient.setAttribute("id", "grad1");
linearGradient.setAttribute("x1", "0%");
linearGradient.setAttribute("y1", "0%");
linearGradient.setAttribute("x2", "100%");
linearGradient.setAttribute("y2", "0%");

// 添加颜色停止点
const stop1 = document.createElementNS(svgNS, "stop");
stop1.setAttribute("offset", "0%");
stop1.setAttribute("style", "stop-color:rgb(255,255,0);stop-opacity:1");
linearGradient.appendChild(stop1);

const stop2 = document.createElementNS(svgNS, "stop");
stop2.setAttribute("offset", "100%");
stop2.setAttribute("style", "stop-color:rgb(255,0,0);stop-opacity:1");
linearGradient.appendChild(stop2);

// 将渐变添加到SVG定义中
svg.appendChild(linearGradient);

// 创建一个矩形并应用渐变
const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("width", "200");
rect.setAttribute("height", "200");
rect.setAttribute("fill", "url(#grad1)");

svg.appendChild(rect);
document.body.appendChild(svg);
```

## 说明
使用 `SVGLinearGradientElement` 时，需要注意以下几点：
- 确保在SVG的 `<defs>` 中定义渐变，以便可以被多个元素重用。
- 渐变的坐标系可能会影响结果，需根据具体需求调整 `gradientUnits` 属性。
- 颜色停止点的顺序和位置会直接影响最终的显示效果。

## 一句话总结
`SVGLinearGradientElement` 是用于在SVG中创建和操作线性渐变的JavaScript接口，提供丰富的视觉效果。