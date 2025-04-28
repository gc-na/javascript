<!--
Meta Description: # DOMRectList：JavaScript 中的矩形列表对象 ## 摘要 `DOMRectList` 是一个用于处理多个 `DOMRect` 对象的集合，常用于获取元素的边界信息，帮助开发者在进行布局和碰撞检测时更好地操作 DOM。 ## 文档 `DOMRectList` 是一个只读的集合，包...
Meta Keywords: domrectlist, getclientrects, domrect, rect, javascript
-->

# DOMRectList：JavaScript 中的矩形列表对象

## 摘要
`DOMRectList` 是一个用于处理多个 `DOMRect` 对象的集合，常用于获取元素的边界信息，帮助开发者在进行布局和碰撞检测时更好地操作 DOM。

## 文档
`DOMRectList` 是一个只读的集合，包含多个 `DOMRect` 对象。每个 `DOMRect` 对象代表一个矩形的边界，包含坐标和尺寸信息（如左边距、上边距、宽度和高度等）。`DOMRectList` 通常由 `getClientRects()` 方法返回，该方法可以在一个元素上调用，以获取该元素的所有可见边界矩形。

### 用法
```javascript
let rects = element.getClientRects();
```
在这个例子中，`element` 是一个 DOM 元素，`getClientRects()` 方法返回一个 `DOMRectList` 对象。

### 属性和方法
- **length**: 返回 `DOMRectList` 中 `DOMRect` 对象的数量。
- **item(index)**: 返回指定索引位置的 `DOMRect` 对象。

## 示例
以下是如何使用 `DOMRectList` 的基本示例：

```javascript
// 获取一个元素
const element = document.getElementById('myElement');

// 获取该元素的所有矩形边界
const rects = element.getClientRects();

// 遍历并输出每个矩形的属性
for (let i = 0; i < rects.length; i++) {
    let rect = rects.item(i);
    console.log(`矩形 ${i}: left=${rect.left}, top=${rect.top}, width=${rect.width}, height=${rect.height}`);
}
```

## 说明
使用 `DOMRectList` 时，开发者需要注意以下几点：
- `DOMRectList` 是动态的，意味着当 DOM 结构变化时，调用 `getClientRects()` 返回的结果也会随之更新。
- `getClientRects()` 只返回可见的矩形，如果元素被隐藏或者没有实际的渲染效果，返回的可能是空的 `DOMRectList`。
- 在处理多个矩形时，务必考虑到可能出现的重叠区域，这在碰撞检测或元素排列时非常重要。

## 一句话总结
`DOMRectList` 是一个在 JavaScript 中用于处理多个矩形边界的集合，主要通过 `getClientRects()` 方法获取。