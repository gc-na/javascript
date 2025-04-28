<!--
Meta Description: # onanimationend：JavaScript 动画结束事件的详解 ## 简介 `onanimationend` 是一个 JavaScript 事件，用于监听 CSS 动画的结束。当动画完成时，该事件被触发，允许开发者在动画结束时执行特定的 JavaScript 代码。 ## 文档 ### ...
Meta Keywords: onanimationend, javascript, css, element, event
-->

# onanimationend：JavaScript 动画结束事件的详解

## 简介
`onanimationend` 是一个 JavaScript 事件，用于监听 CSS 动画的结束。当动画完成时，该事件被触发，允许开发者在动画结束时执行特定的 JavaScript 代码。

## 文档
### 目的
`onanimationend` 事件旨在提供一种方法，让开发者能够在 CSS 动画结束时进行相应的操作，如更新 UI、执行回调函数或触发其他动画。

### 用法
要使用 `onanimationend` 事件，您可以通过以下步骤进行：

1. 选择一个 DOM 元素，该元素上应用了 CSS 动画。
2. 监听 `animationend` 事件。
3. 在事件处理程序中编写所需的 JavaScript 逻辑。

### 详细说明
`onanimationend` 事件会在 CSS 动画完成时触发。该事件的处理程序可以接收一个事件对象，其中包含有关动画的信息。

**事件对象属性：**
- `animationName`：动画的名称。
- `elapsedTime`：动画持续的时间（以秒为单位）。
- `pseudoElement`：伪元素（如 `::before` 或 `::after`），如果适用。

### 语法示例
```javascript
const element = document.getElementById('myElement');

element.onanimationend = function(event) {
    console.log('动画结束:', event.animationName);
    // 在这里添加其他逻辑
};
```

## 示例
### 基本用法
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onanimationend 示例</title>
    <style>
        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }
        .fade {
            animation: fadeOut 2s forwards;
        }
    </style>
</head>
<body>
    <div id="myElement" class="fade">动画正在进行中...</div>

    <script>
        const element = document.getElementById('myElement');

        element.onanimationend = function(event) {
            console.log('动画结束:', event.animationName);
            element.style.display = 'none'; // 动画结束后隐藏元素
        };
    </script>
</body>
</html>
```

## 说明
### 常见陷阱和注意事项
- **事件未触发**：确保所关联的元素确实应用了 CSS 动画，并且动画持续时间大于零。
- **多个动画**：如果元素有多个动画，`onanimationend` 会在每个动画结束时触发。可以使用 `event.animationName` 来区分。
- **使用 `addEventListener`**：建议使用 `addEventListener` 方法来添加事件监听器，以便在需要时可以轻松移除监听器。

## 一句话总结
`onanimationend` 事件允许开发者在 CSS 动画结束时执行特定的 JavaScript 代码，从而增强用户交互体验。