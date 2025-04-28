<!--
Meta Description: # HTMLHRElement: JavaScript 中的水平线元素 ## 摘要 `HTMLHRElement` 是一种 JavaScript 接口，代表 HTML 中的 `<hr>` 元素，用于创建主题分隔线。它可以通过 JavaScript 进行访问和操作，从而动态地控制网页的样式和内容。 #...
Meta Keywords: javascript, htmlhrelement, document, html, 中的水平线元素
-->

# HTMLHRElement: JavaScript 中的水平线元素

## 摘要
`HTMLHRElement` 是一种 JavaScript 接口，代表 HTML 中的 `<hr>` 元素，用于创建主题分隔线。它可以通过 JavaScript 进行访问和操作，从而动态地控制网页的样式和内容。

## 文档
`HTMLHRElement` 接口是 Document Object Model (DOM) 的一部分，专门用于表示和操作 HTML 中的水平线元素。`<hr>` 标签用于在页面中创建水平线，通常用作内容的分隔符。该元素由浏览器默认样式渲染，通常是一个水平线，但其外观可以通过 CSS 进行自定义。

### 目的
- 创建视觉上的分隔效果。
- 提高页面的可读性和结构性。

### 用法
您可以通过 JavaScript 访问和修改 `<hr>` 元素的属性和样式。比如，您可以更改其颜色、宽度或在 DOM 中插入、删除该元素。

### 详细属性
- **align**: 设置水平线的对齐方式（如 "left", "center", "right"）。
- **size**: 设置线的高度（像素）。
- **width**: 设置线的宽度（像素或百分比）。

## 示例
### 创建并插入水平线
```javascript
// 创建一个 <hr> 元素
const hr = document.createElement('hr');

// 设置属性
hr.setAttribute('align', 'center');
hr.setAttribute('width', '50%');

// 将 <hr> 元素添加到页面
document.body.appendChild(hr);
```

### 修改现有的水平线
```javascript
// 获取页面上的第一个 <hr> 元素
const hr = document.querySelector('hr');

// 修改属性
hr.style.borderColor = 'blue';
hr.style.height = '2px';
```

## 说明
- **常见问题**: 当在 CSS 中使用 `margin` 或 `padding` 时，可能会影响 `<hr>` 的位置和大小。
- **注意事项**: `<hr>` 标签是自闭合标签，因此不需要关闭标签。
- **浏览器兼容性**: 所有现代浏览器均支持 `<hr>` 元素，但其默认样式可能会有所不同。

## 一句话总结
`HTMLHRElement` 是 JavaScript 中用于操作 HTML `<hr>` 元素的接口，允许您动态创建和修改网页中的水平分隔线。