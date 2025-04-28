<!--
Meta Description: # CSS 动画与 JavaScript 的关系 ## 概述 CSS 动画（CSS Animation）是一种使用 CSS 技术为 HTML 元素添加动态效果的方式。结合 JavaScript，开发者可以更灵活地控制动画的触发、结束和状态变化，从而实现复杂的用户交互和动效。 ## 文档 ### 目的...
Meta Keywords: css, javascript, html, animated, element
-->

# CSS 动画与 JavaScript 的关系

## 概述
CSS 动画（CSS Animation）是一种使用 CSS 技术为 HTML 元素添加动态效果的方式。结合 JavaScript，开发者可以更灵活地控制动画的触发、结束和状态变化，从而实现复杂的用户交互和动效。

## 文档
### 目的
CSS 动画允许通过简单的 CSS 规则定义元素的过渡效果，而 JavaScript 则提供了动态控制这些动画的能力。通过 JavaScript 可以添加、移除或修改 CSS 类，从而触发相应的动画效果。

### 用法
要使用 CSS 动画，首先需要在 CSS 中定义动画关键帧和相关样式。然后，JavaScript 可以通过操作 DOM 来控制这些动画的播放。

#### CSS 定义
```css
@keyframes example {
    from {background-color: red;}
    to {background-color: yellow;}
}

.animated {
    animation-name: example;
    animation-duration: 4s;
}
```

#### JavaScript 控制
```javascript
const element = document.getElementById('myElement');

// 添加动画类
element.classList.add('animated');

// 移除动画类
setTimeout(() => {
    element.classList.remove('animated');
}, 4000);
```

## 示例
### 基本示例
以下是一个简单的示例，演示如何使用 CSS 动画和 JavaScript 来改变一个元素的背景颜色。

#### HTML 结构
```html
<div id="myElement" style="width:100px; height:100px;"></div>
<button id="startAnimation">开始动画</button>
```

#### 完整代码
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        @keyframes example {
            from {background-color: red;}
            to {background-color: yellow;}
        }

        .animated {
            animation-name: example;
            animation-duration: 4s;
        }
    </style>
    <title>CSS 动画示例</title>
</head>
<body>
    <div id="myElement" style="width:100px; height:100px;"></div>
    <button id="startAnimation">开始动画</button>

    <script>
        const element = document.getElementById('myElement');
        const button = document.getElementById('startAnimation');

        button.onclick = () => {
            element.classList.add('animated');
            setTimeout(() => {
                element.classList.remove('animated');
            }, 4000);
        };
    </script>
</body>
</html>
```

## 说明
- **常见问题**：确保在 CSS 中定义的动画名称与 JavaScript 中使用的类名一致。
- **性能考虑**：使用 CSS 动画比使用 JavaScript 动画更高效，因为它们可以利用 GPU 加速。
- **事件监听**：可以通过 `animationend` 事件来检测动画的结束，这有助于在动画完成后执行其他操作。

## 一句话总结
CSS 动画与 JavaScript 的结合使得网页元素的动态效果更加灵活和强大。