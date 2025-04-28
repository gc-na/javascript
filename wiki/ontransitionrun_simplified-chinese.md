<!--
Meta Description: # ontransitionrun 事件在 JavaScript 中的应用 ## 概述 `ontransitionrun` 是一个用于处理 CSS 过渡动画开始时的事件，在 JavaScript 中被广泛应用于网页的动态效果和用户交互反馈。 ## 文档 `ontransitionrun` 事件在 C...
Meta Keywords: ontransitionrun, css, html, element, myelement
-->

# ontransitionrun 事件在 JavaScript 中的应用

## 概述
`ontransitionrun` 是一个用于处理 CSS 过渡动画开始时的事件，在 JavaScript 中被广泛应用于网页的动态效果和用户交互反馈。

## 文档
`ontransitionrun` 事件在 CSS 过渡动画开始执行时触发。它是 `HTMLElement` 接口的一部分，允许开发者在过渡效果开始时进行特定的操作，比如添加额外的样式、记录状态等。

### 目的
该事件的主要目的在于实现实时反馈，允许开发者在动画开始时执行代码，以便更好地控制用户体验。

### 用法
要使用 `ontransitionrun` 事件，您可以将其添加到任何支持 CSS 过渡的 HTML 元素上。以下是基本的使用方法：

```javascript
const element = document.getElementById('myElement');

element.ontransitionrun = function(event) {
    console.log('过渡动画开始:', event.propertyName);
};
```

### 详细信息
- **事件对象**：当 `ontransitionrun` 事件被触发时，会传递一个事件对象，该对象包含了相关的属性和方法。
- **属性**：
  - `propertyName`：一个字符串，表示正在过渡的 CSS 属性的名称。
  - `target`：触发事件的元素。
  
## 示例
以下是一个基本示例，展示如何使用 `ontransitionrun` 事件：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ontransitionrun 示例</title>
    <style>
        #myElement {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .change {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div id="myElement"></div>
    <button id="toggleButton">切换颜色</button>

    <script>
        const element = document.getElementById('myElement');
        const button = document.getElementById('toggleButton');

        element.ontransitionrun = function(event) {
            console.log('过渡动画开始:', event.propertyName);
        };

        button.addEventListener('click', function() {
            element.classList.toggle('change');
        });
    </script>
</body>
</html>
```

在这个示例中，点击按钮会切换 `myElement` 的背景颜色，并在过渡动画开始时输出相关信息。

## 说明
在使用 `ontransitionrun` 时，开发者应注意以下几点：
- 确保元素确实具有 CSS 过渡效果，否则事件不会触发。
- 该事件在每次过渡开始时都会被触发，因此可能需要在事件处理函数中进行去重或状态管理，以避免不必要的操作。

## 一句话总结
`ontransitionrun` 事件在 CSS 过渡动画开始时触发，允许开发者在动画开始时执行特定的操作。