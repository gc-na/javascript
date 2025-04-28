<!--
Meta Description: # pageYOffset：JavaScript 中的页面垂直滚动位置 ## 概述 `pageYOffset` 是一个全局属性，用于获取文档相对于视口的垂直滚动位置。它在网页滚动时非常有用，可以帮助开发者实现平滑滚动或动态效果。 ## 文档 `pageYOffset` 是一个只读属性，返回当前文档的...
Meta Keywords: pageyoffset, window, javascript, scrollposition, let
-->

# pageYOffset：JavaScript 中的页面垂直滚动位置

## 概述
`pageYOffset` 是一个全局属性，用于获取文档相对于视口的垂直滚动位置。它在网页滚动时非常有用，可以帮助开发者实现平滑滚动或动态效果。

## 文档
`pageYOffset` 是一个只读属性，返回当前文档的垂直滚动距离（以像素为单位）。其值为文档顶部到视口顶部的距离。当页面未滚动时，`pageYOffset` 的值为 0。

### 用法
- 语法：`window.pageYOffset`
- 返回值：一个非负整数，表示当前文档的垂直滚动量。

### 适用场景
- 检测用户的滚动位置，以改变页面元素的样式或行为。
- 实现无限滚动加载功能。
- 创建导航栏在滚动时固定在顶部的效果。

## 示例
```javascript
// 获取当前页面的垂直滚动位置
let scrollPosition = window.pageYOffset;
console.log(scrollPosition);
```

```javascript
// 在用户滚动页面时，输出当前的滚动位置
window.addEventListener('scroll', function() {
    console.log('当前滚动位置:', window.pageYOffset);
});
```

```javascript
// 根据滚动位置改变元素的透明度
window.addEventListener('scroll', function() {
    let scrollPosition = window.pageYOffset;
    let opacity = 1 - scrollPosition / 500; // 500像素后元素完全透明
    document.getElementById('myElement').style.opacity = opacity;
});
```

## 说明
- `pageYOffset` 仅在支持的浏览器中有效，所有现代浏览器均支持此属性，但在某些旧版浏览器中可能不可用。
- 注意，`pageYOffset` 始终返回数字，若页面没有滚动，则返回值为 0。
- 对于某些情况下（如使用 CSS 的 `overflow: hidden`），`pageYOffset` 可能不会按预期工作。

## 一句话总结
`pageYOffset` 是用于获取当前文档垂直滚动位置的 JavaScript 属性。