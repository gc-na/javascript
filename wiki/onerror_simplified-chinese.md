<!--
Meta Description: # JavaScript 的 onerror 事件处理程序详解 ## 概述 `onerror` 是 JavaScript 中用于处理错误事件的一个重要属性。它可以帮助开发者捕获和处理运行时错误，从而提高应用程序的稳定性和用户体验。 ## 文档 ### 目的 `onerror` 主要用于捕获网页中的 ...
Meta Keywords: onerror, javascript, html, message, src
-->

# JavaScript 的 onerror 事件处理程序详解

## 概述
`onerror` 是 JavaScript 中用于处理错误事件的一个重要属性。它可以帮助开发者捕获和处理运行时错误，从而提高应用程序的稳定性和用户体验。

## 文档
### 目的
`onerror` 主要用于捕获网页中的 JavaScript 错误。当一个脚本发生错误时，`onerror` 事件处理程序会被触发，允许开发者进行自定义的错误处理。

### 使用
`onerror` 可以在全局范围内使用，也可以为特定的 HTML 元素设置。以下是两种常见的用法：

1. **全局 `onerror`**：
   你可以在全局作用域中定义一个 `onerror` 函数，这样所有未捕获的错误都会被这个函数处理。
   ```javascript
   window.onerror = function(message, source, lineno, colno, error) {
       console.error('发生错误:', message);
   };
   ```

2. **特定元素的 `onerror`**：
   你也可以为特定的 HTML 元素，比如 `<img>` 标签，设置 `onerror` 事件处理程序，用于处理加载错误。
   ```html
   <img src="invalid-image.jpg" onerror="this.onerror=null; this.src='fallback-image.jpg';">
   ```

### 详细信息
- `onerror` 处理程序可以接收多个参数，包括错误信息、错误源、行号、列号和错误对象。
- 此事件处理程序的返回值可以是布尔值，用于指示错误是否被处理。
- 在处理图片加载错误时，可以防止多次触发错误处理程序，将 `this.onerror` 设置为 `null`。

## 示例
### 全局错误处理
```javascript
window.onerror = function(message, source, lineno, colno, error) {
    alert(`错误发生在 ${source} 的第 ${lineno} 行: ${message}`);
};
```

### 图片加载错误处理
```html
<img src="nonexistent.jpg" onerror="this.src='default.jpg'; alert('图片加载失败，已更换为默认图片。');">
```

## 说明
1. **常见问题**：
   - 如果在 `onerror` 中抛出错误，可能会导致无限循环，因此在处理错误时应小心。
   
2. **注意事项**：
   - `onerror` 只捕获未处理的错误，对于 `try...catch` 中捕获的错误不会触发。
   - 在某些情况下，浏览器的安全策略可能会限制 `onerror` 的执行。

## 一句话总结
`onerror` 是 JavaScript 中用于捕获和处理运行时错误的重要工具，能够显著提升应用程序的稳定性。