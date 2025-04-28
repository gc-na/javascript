<!--
Meta Description: # JavaScript 的 innerHeight 属性详解 ## 概述 `innerHeight` 是一个用于获取浏览器窗口内部高度的属性，单位为像素。它是 `window` 对象的一个属性，常用于响应式设计和动态布局中。 ## 文档 ### 目的 `innerHeight` 主要用于获取当前浏...
Meta Keywords: innerheight, window, javascript, let, windowheight
-->

# JavaScript 的 innerHeight 属性详解

## 概述
`innerHeight` 是一个用于获取浏览器窗口内部高度的属性，单位为像素。它是 `window` 对象的一个属性，常用于响应式设计和动态布局中。

## 文档
### 目的
`innerHeight` 主要用于获取当前浏览器窗口的可视高度，允许开发者根据窗口尺寸调整页面内容。

### 用法
`innerHeight` 的基本用法如下：
```javascript
let height = window.innerHeight;
```

### 详细说明
- **返回值**：`innerHeight` 返回一个数字，表示浏览器窗口的内部高度，包括滚动条（如果存在）。
- **读取值**：可以直接使用 `window.innerHeight` 来获取当前窗口的高度。
- **动态变化**：当浏览器窗口大小发生变化时，`innerHeight` 的值也会随之更新，适合在窗口调整时进行重新布局。
- **浏览器支持**：现代浏览器均支持 `innerHeight` 属性，但在某些老旧浏览器中可能不兼容。

## 示例
以下是使用 `innerHeight` 的基本示例：

### 示例 1: 获取窗口高度
```javascript
let windowHeight = window.innerHeight;
console.log("当前窗口高度: " + windowHeight + " 像素");
```

### 示例 2: 窗口大小变化时动态获取高度
```javascript
window.addEventListener('resize', () => {
    console.log("新窗口高度: " + window.innerHeight + " 像素");
});
```

## 说明
- **常见陷阱**：在某些情况下，`innerHeight` 可能不包括工具栏或其他浏览器界面元素的高度。这可能导致获取的高度与实际可视区域不完全一致。
- **与 `outerHeight` 的区别**：`outerHeight` 返回整个浏览器窗口的高度，包括工具栏和滚动条，而 `innerHeight` 仅返回可视区域的高度。
- **适用场景**：在开发响应式网页时，`innerHeight` 可以帮助开发者做出适应不同屏幕尺寸的布局调整。

## 一句话总结
`innerHeight` 是 JavaScript 中用于获取浏览器窗口内部可视高度的属性，常用于动态布局。