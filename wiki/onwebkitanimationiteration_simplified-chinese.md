<!--
Meta Description: # onwebkitAnimationIteration: JavaScript 动画事件处理 ## 概述 `onwebkitAnimationIteration` 是一个 JavaScript 事件处理程序属性，用于在 CSS 动画每次迭代完成后触发特定的 JavaScript 代码。它是与 We...
Meta Keywords: onwebkitanimationiteration, javascript, css, webkit, html
-->

# onwebkitAnimationIteration: JavaScript 动画事件处理

## 概述
`onwebkitAnimationIteration` 是一个 JavaScript 事件处理程序属性，用于在 CSS 动画每次迭代完成后触发特定的 JavaScript 代码。它是与 WebKit 浏览器相关的前缀，用于处理动画的迭代过程。

## 文档
### 目的
`onwebkitAnimationIteration` 允许开发者在 CSS 动画完成一次迭代后执行自定义的 JavaScript 代码。此事件在每次动画循环结束时被触发，适用于需要在动画进行过程中执行操作的场景。

### 使用方法
要使用 `onwebkitAnimationIteration`，可以将其作为事件处理程序附加到一个 DOM 元素上。以下是基本的使用步骤：

1. 在 CSS 中定义动画。
2. 在 JavaScript 中获取目标元素。
3. 为该元素设置 `onwebkitAnimationIteration` 属性，指定一个函数来处理事件。

### 详细说明
- **事件类型**：`webkitAnimationIteration` 事件。
- **兼容性**：此事件主要用于 WebKit 内核的浏览器（如 Safari 和旧版本的 Chrome）。现代浏览器通常使用标准的 `animationiteration` 事件。
- **注意事项**：确保为元素添加动画的 CSS 属性，并在 JavaScript 中正确处理事件。

## 示例
### 基本用法
以下是一个简单的示例，展示如何使用 `onwebkitAnimationIteration`：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onwebkitAnimationIteration 示例</title>
    <style>
        .animate {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: myAnimation 2s infinite;
        }

        @keyframes myAnimation {
            0% { transform: translateX(0); }
            100% { transform: translateX(100px); }
        }
    </style>
</head>
<body>
    <div class="animate" id="myBox"></div>

    <script>
        const box = document.getElementById('myBox');

        box.onwebkitAnimationIteration = function() {
            console.log('动画迭代完成一次！');
        };
    </script>
</body>
</html>
```

## 说明
- **常见问题**：在使用 `onwebkitAnimationIteration` 时，需要注意动画是否已正确应用于元素。如果动画未能正常执行，事件可能不会被触发。
- **兼容性问题**：由于 `onwebkitAnimationIteration` 是特定于 WebKit 的，因此在其他浏览器中可能无效。建议同时实现标准的 `animationiteration` 事件以确保跨浏览器兼容性。

## 一句话总结
`onwebkitAnimationIteration` 是一个用于在 CSS 动画迭代完成后触发 JavaScript 代码的事件处理程序，适用于 WebKit 浏览器。