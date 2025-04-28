<!--
Meta Description: # JavaScript中的CanvasGradient：创建和使用渐变色 ## 概述 CanvasGradient 是 HTML5 Canvas API 中的重要组成部分，用于创建颜色渐变效果。它允许开发者在 Canvas 上绘制平滑的颜色过渡，增强图形的视觉效果。 ## 文档 CanvasGra...
Meta Keywords: gradient, canvas, ctx, addcolorstop, const
-->

# JavaScript中的CanvasGradient：创建和使用渐变色

## 概述
CanvasGradient 是 HTML5 Canvas API 中的重要组成部分，用于创建颜色渐变效果。它允许开发者在 Canvas 上绘制平滑的颜色过渡，增强图形的视觉效果。

## 文档
CanvasGradient 对象用于定义颜色渐变。它支持线性渐变和放射性渐变。开发者可以通过 Canvas 的 `createLinearGradient()` 和 `createRadialGradient()` 方法来创建渐变对象，并通过 `addColorStop()` 方法添加颜色停止点。

### 目的
CanvasGradient 的主要目的是为绘图提供渐变效果，提升图形的美感和层次感。

### 用法
1. **创建渐变**：
   - 线性渐变：使用 `createLinearGradient(x0, y0, x1, y1)` 创建一个从 `(x0, y0)` 到 `(x1, y1)` 的线性渐变。
   - 放射性渐变：使用 `createRadialGradient(x0, y0, r0, x1, y1, r1)` 创建一个从 `(x0, y0)` 半径为 `r0` 的圆形到 `(x1, y1)` 半径为 `r1` 的圆形的渐变。

2. **添加颜色停止点**：
   - 使用 `gradient.addColorStop(offset, color)` 方法，`offset` 为 0 到 1 之间的值，表示渐变的进度，`color` 为填充的颜色。

### 详细属性
- **线性渐变**：通过定义两个点来创建。
- **放射性渐变**：通过定义两个圆形来创建。
- **颜色停止点**：可以定义多个颜色，且每个颜色的具体位置可以精确控制。

## 示例
### 线性渐变示例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 100);
```

### 放射性渐变示例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createRadialGradient(75, 75, 25, 90, 90, 100);
gradient.addColorStop(0, 'yellow');
gradient.addColorStop(1, 'green');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 200);
```

## 解释
在使用 CanvasGradient 时，开发者需要注意以下几点：
- 渐变的颜色停止点必须在 0 到 1 的范围内，超出这个范围可能导致意想不到的效果。
- 在同一个 Canvas 上创建多个渐变时，需要确保每个渐变的定义不会冲突。
- 渐变的颜色可以使用任何有效的 CSS 颜色格式（如 HEX、RGB、RGBA、HSL等）。

## 一句话总结
CanvasGradient 是 JavaScript 中用于创建丰富渐变效果的强大工具，能够提升图形的视觉吸引力。