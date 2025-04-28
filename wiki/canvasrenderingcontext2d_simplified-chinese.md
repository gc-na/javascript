<!--
Meta Description: # CanvasRenderingContext2D：JavaScript 中的 2D 渲染上下文 ## 概述 `CanvasRenderingContext2D` 是 HTML5 中提供的一个接口，用于在 `<canvas>` 元素上绘制 2D 图形和图像。通过该接口，开发者可以使用 JavaSc...
Meta Keywords: ctx, canvas, javascript, fillstyle, canvasrenderingcontext2d
-->

# CanvasRenderingContext2D：JavaScript 中的 2D 渲染上下文

## 概述
`CanvasRenderingContext2D` 是 HTML5 中提供的一个接口，用于在 `<canvas>` 元素上绘制 2D 图形和图像。通过该接口，开发者可以使用 JavaScript 创建复杂的图形、动画和游戏。

## 文档
`CanvasRenderingContext2D` 提供了一系列方法和属性，允许开发者绘制形状、文本、图像并进行多种操作，如旋转、缩放和裁剪。使用 `getContext("2d")` 方法来获取该上下文。

### 主要用途
- 绘制矩形、圆形、路径等基本形状
- 绘制文本
- 加载和显示图像
- 实现图形变换（如缩放、旋转）
- 创建渐变和图案

### 使用方法
1. **创建 `<canvas>` 元素：**
   ```html
   <canvas id="myCanvas" width="500" height="500"></canvas>
   ```

2. **获取上下文：**
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   ```

3. **绘制示例：**
   ```javascript
   ctx.fillStyle = 'blue';
   ctx.fillRect(10, 10, 100, 100); // 绘制蓝色矩形
   ```

## 示例
### 示例 1：绘制矩形
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'green';
ctx.fillRect(20, 20, 150, 100); // 绘制绿色矩形
```

### 示例 2：绘制圆形
```javascript
ctx.beginPath();
ctx.arc(200, 200, 50, 0, Math.PI * 2); // 绘制圆
ctx.fillStyle = 'red';
ctx.fill();
```

### 示例 3：绘制文本
```javascript
ctx.font = '30px Arial';
ctx.fillStyle = 'black';
ctx.fillText('Hello, Canvas!', 10, 50); // 绘制文本
```

## 解释
常见的问题包括：
- **上下文未正确获取**：确保调用 `getContext('2d')` 正确地获取 2D 上下文。
- **绘制顺序错误**：绘图顺序会影响最终显示，后绘制的图形会覆盖之前的图形。
- **未设置填充样式**：在绘制填充形状之前，确保设置了 `fillStyle`。
- **设备像素比例**：在高 DPI 设备上，可能需要调整 `<canvas>` 的实际像素大小，以避免模糊。

## 一句话总结
`CanvasRenderingContext2D` 是一个强大的接口，用于在 HTML5 `<canvas>` 元素上绘制和操作 2D 图形。