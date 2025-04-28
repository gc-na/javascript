<!--
Meta Description: # JavaScript 中的 onunload 事件详解 ## 摘要 `onunload` 事件是 JavaScript 中的一个事件处理程序，用于在用户离开页面时执行特定的 JavaScript 代码。 ## 文档 ### 目的 `onunload` 事件在用户关闭浏览器窗口、标签页，或导航到其...
Meta Keywords: onunload, html, javascript, body, head
-->

# JavaScript 中的 onunload 事件详解

## 摘要
`onunload` 事件是 JavaScript 中的一个事件处理程序，用于在用户离开页面时执行特定的 JavaScript 代码。

## 文档
### 目的
`onunload` 事件在用户关闭浏览器窗口、标签页，或导航到其他页面时被触发。这个事件可以用于保存用户的状态、清理资源或进行日志记录等操作。

### 用法
`onunload` 事件可以通过 HTML 属性或 JavaScript 代码进行设置。以下是两种常见的设置方法：

1. **HTML 属性**:
   ```html
   <body onunload="myFunction()">
   ```

2. **JavaScript 代码**:
   ```javascript
   window.onunload = function() {
       // 执行某些操作
   };
   ```

### 详细说明
- `onunload` 事件在页面完全卸载之前被触发。
- 由于安全性和用户体验，某些浏览器可能会对 `onunload` 事件中的某些操作进行限制。
- 该事件通常用于执行清理工作，例如取消计时器或关闭 WebSocket 连接。

## 示例
### 示例 1: 使用 HTML 属性
```html
<!DOCTYPE html>
<html>
<head>
    <title>onunload 示例</title>
</head>
<body onunload="alert('您正在离开页面！')">
    <h1>欢迎访问我的网站</h1>
</body>
</html>
```

### 示例 2: 使用 JavaScript
```html
<!DOCTYPE html>
<html>
<head>
    <title>onunload 示例</title>
    <script>
        window.onunload = function() {
            console.log('页面即将卸载');
        };
    </script>
</head>
<body>
    <h1>欢迎访问我的网站</h1>
</body>
</html>
```

## 解释
- **常见问题**:
  - 在某些情况下，`onunload` 事件可能不会触发。例如，用户直接关闭浏览器或使用 Ctrl+W 关闭标签页时。
  - 某些浏览器的安全策略可能限制在 `onunload` 中执行的操作，比如弹出窗口。

- **注意事项**:
  - 尽量避免在 `onunload` 事件中执行阻塞性操作，因为这会影响用户体验。
  - 对于需要在页面卸载时执行的异步操作，建议使用 `beforeunload` 事件来处理。

## 一句话总结
`onunload` 事件用于在用户离开页面时触发特定的 JavaScript 代码，以进行清理或状态保存。