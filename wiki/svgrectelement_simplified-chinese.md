<!--
Meta Description: # SVGRectElement: JavaScript 中的矩形元素 ## 概述 `SVGRectElement` 是一种用于创建和操作 SVG（可缩放矢量图形）中矩形的接口。在 JavaScript 中，可以通过 DOM 操作来访问和修改这些矩形元素，从而实现动态图形效果。 ## 文档 ### ...
Meta Keywords: svg, setattribute, rect, svgrectelement, javascript
-->

# SVGRectElement: JavaScript 中的矩形元素

## 概述
`SVGRectElement` 是一种用于创建和操作 SVG（可缩放矢量图形）中矩形的接口。在 JavaScript 中，可以通过 DOM 操作来访问和修改这些矩形元素，从而实现动态图形效果。

## 文档
### 目的
`SVGRectElement` 代表 SVG 中的矩形元素。它继承自 `SVGShapeElement`，并提供了创建和管理矩形的属性和方法。

### 用法
`SVGRectElement` 主要用于定义和控制矩形的外观和位置。以下是一些常用的属性和方法：

- **属性**:
  - `x`: 矩形的 x 坐标。
  - `y`: 矩形的 y 坐标。
  - `width`: 矩形的宽度。
  - `height`: 矩形的高度。
  - `rx`: 矩形的圆角半径（x 轴）。
  - `ry`: 矩形的圆角半径（y 轴）。

- **方法**:
  - `getBBox()`: 返回矩形的边界框。
  - `setAttribute()`: 用于设置矩形的属性。

### 示例
以下是使用 `SVGRectElement` 的一些基本示例：

```javascript
// 创建 SVG 容器
const svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");
document.body.appendChild(svg);

// 创建矩形
const rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("x", "10");
rect.setAttribute("y", "10");
rect.setAttribute("width", "100");
rect.setAttribute("height", "50");
rect.setAttribute("fill", "blue");

// 将矩形添加到 SVG 容器
svg.appendChild(rect);
```

### 说明
在使用 `SVGRectElement` 时，有一些常见的误区需要注意：

1. **坐标系**: SVG 使用的是左上角为原点的坐标系，坐标值越大，位置越向右和向下移动。
2. **单位问题**: 默认情况下，SVG 的尺寸是以像素为单位，但可以使用其他单位（如百分比）来定义位置和尺寸。
3. **样式**: 矩形的填充和边框样式可以通过 `fill` 和 `stroke` 属性设置。确保在使用 CSS 时考虑到 SVG 的特性。

## 一句话总结
`SVGRectElement` 是 JavaScript 中用于创建和操作 SVG 矩形元素的接口。