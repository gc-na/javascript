<!--
Meta Description: # DOMRectReadOnly：JavaScript 中的只读矩形对象 ## 概述 `DOMRectReadOnly` 是一个用于表示矩形区域的 JavaScript 对象，通常用于获取元素的大小和位置。这种只读数据结构提供了矩形的边界属性，允许开发者在处理布局和碰撞检测时高效地访问元素的几何信...
Meta Keywords: rect, domrectreadonly, getboundingclientrect, console, log
-->

# DOMRectReadOnly：JavaScript 中的只读矩形对象

## 概述
`DOMRectReadOnly` 是一个用于表示矩形区域的 JavaScript 对象，通常用于获取元素的大小和位置。这种只读数据结构提供了矩形的边界属性，允许开发者在处理布局和碰撞检测时高效地访问元素的几何信息。

## 文档
### 目的
`DOMRectReadOnly` 的主要目的是提供一个不可变的矩形区域表示。它通常由浏览器的 API 生成，如 `getBoundingClientRect()`，用于返回元素相对于视口的大小和位置。

### 用法
`DOMRectReadOnly` 对象包含以下属性：

- `x`：矩形左上角的 x 坐标。
- `y`：矩形左上角的 y 坐标。
- `width`：矩形的宽度。
- `height`：矩形的高度。
- `top`：矩形顶部的 y 坐标。
- `right`：矩形右侧的 x 坐标。
- `bottom`：矩形底部的 y 坐标。
- `left`：矩形左侧的 x 坐标。

这些属性均为只读，意味着一旦 `DOMRectReadOnly` 对象创建后，其值不可更改。

### 详细信息
`DOMRectReadOnly` 通常由以下方法生成：
- `Element.getBoundingClientRect()`：返回元素的大小及其相对于视口的位置。

```javascript
const rect = element.getBoundingClientRect();
console.log(rect.width, rect.height, rect.x, rect.y);
```

## 示例
以下是 `DOMRectReadOnly` 的基本用法示例：

```javascript
// 获取某个元素的边界矩形
const element = document.querySelector('#myElement');
const rect = element.getBoundingClientRect();

// 输出矩形的各种属性
console.log('Width:', rect.width);     // 输出宽度
console.log('Height:', rect.height);   // 输出高度
console.log('Top:', rect.top);         // 输出顶部坐标
console.log('Left:', rect.left);       // 输出左侧坐标
```

## 解释
在使用 `DOMRectReadOnly` 时，需要注意以下几点：

- **只读特性**：属性是只读的，无法直接修改。如果需要更新矩形的值，必须重新调用生成方法。
- **视口依赖性**：矩形的坐标是相对于视口的，因此如果页面滚动，矩形的值也会发生变化。
- **性能**：多次调用 `getBoundingClientRect()` 可能会影响性能，特别是在动画或高频率的更新中，建议缓存结果。

## 一句话总结
`DOMRectReadOnly` 是一个用于表示元素几何信息的只读矩形对象，常用于获取元素的大小和位置。