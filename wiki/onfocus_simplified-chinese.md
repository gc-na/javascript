<!--
Meta Description: # JavaScript 的 onfocus 事件详解 ## 概述 `onfocus` 是一个在 JavaScript 中广泛使用的事件，用于处理当元素获得焦点时的交互。它通常应用于输入框、文本区域及其他可交互元素，以增强用户体验。 ## 文档 `onfocus` 事件在用户将光标移动到输入元素上时...
Meta Keywords: onfocus, html, javascript, inputelement, myinput
-->

# JavaScript 的 onfocus 事件详解

## 概述
`onfocus` 是一个在 JavaScript 中广泛使用的事件，用于处理当元素获得焦点时的交互。它通常应用于输入框、文本区域及其他可交互元素，以增强用户体验。

## 文档
`onfocus` 事件在用户将光标移动到输入元素上时触发。这一事件通常用于输入验证、样式改变或其他需要在用户开始输入时进行的操作。

### 用法
`onfocus` 可以在 HTML 元素中直接使用，也可以通过 JavaScript 进行绑定。以下是基本的用法示例：

```html
<input type="text" onfocus="myFunction()">
```

在 JavaScript 中，可以使用 `addEventListener` 方法来绑定 `onfocus` 事件：

```javascript
var inputElement = document.getElementById('myInput');
inputElement.addEventListener('focus', myFunction);
```

### 事件对象
当 `onfocus` 事件触发时，可以通过事件对象访问相关信息，例如目标元素、事件类型等。

## 示例
以下是一些基本的使用示例：

### 示例 1：简单的焦点事件
```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>onfocus 示例</title>
</head>
<body>
    <input type="text" id="myInput" onfocus="alert('输入框获得焦点！')">
</body>
</html>
```

### 示例 2：使用 JavaScript 绑定事件
```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>onfocus 示例</title>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        var inputElement = document.getElementById('myInput');
        inputElement.addEventListener('focus', function() {
            this.style.border = '2px solid blue';
        });
    </script>
</body>
</html>
```

## 说明
- **兼容性**：`onfocus` 在大多数现代浏览器中都得到支持，但在某些移动设备上，焦点事件的表现可能与桌面浏览器略有不同。
- **失去焦点**：通常，`onfocus` 与 `onblur` 事件配合使用，以处理元素失去焦点时的行为。
- **可访问性**：确保在使用焦点事件时，考虑到所有用户的可访问性，避免因焦点变化而导致的用户体验下降。

## 一句话总结
`onfocus` 事件用于处理元素获得焦点时的交互，提升用户体验。