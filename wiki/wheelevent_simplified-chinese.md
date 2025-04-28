<!--
Meta Description: # WheelEvent：JavaScript 中的滚轮事件 ## 概述 WheelEvent 是 JavaScript 中用于处理鼠标滚轮事件的接口。它允许开发者获取关于滚轮操作的详细信息，如滚动的方向和距离，进而可以根据用户的交互创建更为丰富的网页体验。 ## 文档 ### 目的 WheelEv...
Meta Keywords: event, wheelevent, javascript, wheel, deltay
-->

# WheelEvent：JavaScript 中的滚轮事件

## 概述
WheelEvent 是 JavaScript 中用于处理鼠标滚轮事件的接口。它允许开发者获取关于滚轮操作的详细信息，如滚动的方向和距离，进而可以根据用户的交互创建更为丰富的网页体验。

## 文档
### 目的
WheelEvent 主要用于处理用户通过鼠标滚轮进行的交互操作，适用于实现平滑滚动、缩放图像或其它需要基于滚轮输入的功能。

### 使用方法
WheelEvent 事件可以通过添加事件监听器来使用。主要的事件类型是 `wheel`，它会在用户滚动鼠标滚轮时触发。

```javascript
element.addEventListener('wheel', function(event) {
    // 事件处理
});
```

### WheelEvent 属性
- `deltaX`：表示水平方向上的滚动量。
- `deltaY`：表示垂直方向上的滚动量。
- `deltaZ`：表示第三个维度上的滚动量（通常用于3D滚动）。
- `ctrlKey`：布尔值，指示在事件发生时是否按下了 Ctrl 键。
- `altKey`：布尔值，指示在事件发生时是否按下了 Alt 键。
- `shiftKey`：布尔值，指示在事件发生时是否按下了 Shift 键。
- `metaKey`：布尔值，指示在事件发生时是否按下了 Meta 键（通常是 Windows 的徽标键或 Mac 的 Command 键）。

## 示例
### 基本使用示例
以下是一个简单的滚轮事件处理示例：

```javascript
const box = document.getElementById('scrollable-box');

box.addEventListener('wheel', function(event) {
    event.preventDefault(); // 防止默认滚动行为
    const delta = event.deltaY;
    
    if (delta > 0) {
        console.log('向下滚动');
    } else {
        console.log('向上滚动');
    }
});
```

### 缩放示例
通过滚轮事件实现图像缩放的示例：

```javascript
const image = document.getElementById('zoomable-image');
let scale = 1;

image.addEventListener('wheel', function(event) {
    event.preventDefault();
    scale += event.deltaY > 0 ? -0.1 : 0.1; // 向下滚动缩小，向上滚动放大
    image.style.transform = `scale(${scale})`;
});
```

## 说明
### 常见问题
- **滚动方向**：`deltaY` 的值可以是正数或负数，正数表示向下滚动，负数表示向上滚动。注意，某些设备（如触控板）可能会产生不同的值。
- **默认行为**：使用 `event.preventDefault()` 可以阻止浏览器的默认滚动行为，以便实现自定义的滚动逻辑。
- **跨浏览器兼容性**：尽管大多数现代浏览器都支持 WheelEvent，但在较旧的浏览器中可能会有兼容性问题，建议做必要的测试。

## 一句话总结
WheelEvent 是 JavaScript 中用于处理鼠标滚轮交互的事件，允许开发者获取详细的滚动信息以增强用户体验。