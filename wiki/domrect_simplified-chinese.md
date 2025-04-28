<!--
Meta Description: # DOMRect：JavaScript中的矩形对象 ## 摘要 DOMRect 是一个用于表示矩形区域的对象，包含矩形的边界信息（如位置和尺寸）。在 JavaScript 中，它通常与元素的几何属性结合使用，便于进行复杂的图形和布局计算。 ## 文档 ### 目的 DOMRect 提供了一个简洁的...
Meta Keywords: domrect, rect, console, log, javascript
-->

# DOMRect：JavaScript中的矩形对象

## 摘要
DOMRect 是一个用于表示矩形区域的对象，包含矩形的边界信息（如位置和尺寸）。在 JavaScript 中，它通常与元素的几何属性结合使用，便于进行复杂的图形和布局计算。

## 文档
### 目的
DOMRect 提供了一个简洁的方法来获取和表示元素在文档中的位置和尺寸。它的属性使开发者能够轻松地访问矩形的左、上、右、下、宽度和高度等信息。

### 用法
DOMRect 通常通过调用元素的 `getBoundingClientRect()` 方法获得。该方法返回一个 DOMRect 对象，表示元素的大小和相对于视口的位置。

### 属性
- **x**：矩形左上角的 x 坐标。
- **y**：矩形左上角的 y 坐标。
- **width**：矩形的宽度。
- **height**：矩形的高度。
- **top**：矩形上边界的 y 坐标。
- **right**：矩形右边界的 x 坐标。
- **bottom**：矩形下边界的 y 坐标。
- **left**：矩形左边界的 x 坐标。

### 示例
```javascript
// 获取一个元素的 DOMRect
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();

// 输出矩形的属性
console.log('Width:', rect.width);
console.log('Height:', rect.height);
console.log('Top:', rect.top);
console.log('Left:', rect.left);
```

### 解释
使用 `DOMRect` 时，开发者需注意以下事项：
- `getBoundingClientRect()` 返回的坐标是相对于视口（viewport）的，而不是文档（document）的，因此在处理滚动的情况下，结果可能会有所不同。
- 在不同的设备和浏览器中，可能会存在微小的差异，尤其是在处理缩放或高 DPI 显示器时。
- `DOMRect` 对象是一个只读对象，不能直接修改其属性。

## 一句话总结
DOMRect 是 JavaScript 中用于表示和操作元素边界的矩形对象，提供了便捷的几何属性访问。