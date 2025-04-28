<!--
Meta Description: # ontransitionend 事件在 JavaScript 中的应用 ## 概述 `ontransitionend` 是一个用于检测 CSS 过渡效果完成的事件。它在 JavaScript 中非常有用，可以帮助开发者在动画结束时执行特定的操作，从而提升用户体验。 ## 文档 ### 目的 `o...
Meta Keywords: ontransitionend, javascript, css, box, event
-->

# ontransitionend 事件在 JavaScript 中的应用

## 概述
`ontransitionend` 是一个用于检测 CSS 过渡效果完成的事件。它在 JavaScript 中非常有用，可以帮助开发者在动画结束时执行特定的操作，从而提升用户体验。

## 文档
### 目的
`ontransitionend` 事件允许开发者监听元素的 CSS 过渡效果何时完成。通过该事件，可以在动画结束时触发相应的 JavaScript 代码，进而实现更复杂的交互。

### 用法
在 JavaScript 中，可以通过添加事件监听器来使用 `ontransitionend` 事件。此事件可以应用于任何带有 CSS 过渡效果的元素。

#### 语法
```javascript
element.addEventListener('transitionend', function(event) {
    // 动画结束后的代码
});
```

### 事件属性
- **propertyName**: 完成过渡的 CSS 属性名称。
- **elapsedTime**: 动画持续的时间，以秒为单位。
- **pseudoElement**: 如果应用于伪元素，则返回该伪元素的名称。

## 示例
### 基本用法示例
以下示例展示了如何使用 `ontransitionend` 事件来监听一个元素的过渡效果完成：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>ontransitionend 示例</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 1s ease;
        }
        .box.active {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="box" id="myBox"></div>
    <button id="toggle">切换颜色</button>

    <script>
        const box = document.getElementById('myBox');
        const button = document.getElementById('toggle');

        button.addEventListener('click', () => {
            box.classList.toggle('active');
        });

        box.addEventListener('transitionend', (event) => {
            console.log(`过渡完成: ${event.propertyName}`);
        });
    </script>
</body>
</html>
```

## 说明
### 常见问题
- **事件未触发**: 确保元素确实具有 CSS 过渡效果，并且相应的属性在过渡期间发生了变化。
- **多个过渡**: 如果一个元素具有多个过渡，`ontransitionend` 可能会被触发多次。可以通过 `event.propertyName` 属性来判断是否是你关心的属性。
- **过渡时间**: 如果在过渡完成之前移除了元素或其样式，可能会导致事件未被触发。

## 一句话总结
`ontransitionend` 是一个用于监听 CSS 过渡效果完成的 JavaScript 事件，帮助开发者在动画结束时执行特定操作。