<!--
Meta Description: # requestAnimationFrame：JavaScript 中优化动画性能的关键方法 ## 概述 `requestAnimationFrame` 是一个用于创建平滑动画效果的 JavaScript 方法。它通过在浏览器的下一个重绘周期中调用指定的回调函数，从而优化动画性能和流畅度。 ## ...
Meta Keywords: requestanimationframe, javascript, start, animate, timestamp
-->

# requestAnimationFrame：JavaScript 中优化动画性能的关键方法

## 概述
`requestAnimationFrame` 是一个用于创建平滑动画效果的 JavaScript 方法。它通过在浏览器的下一个重绘周期中调用指定的回调函数，从而优化动画性能和流畅度。

## 文档
### 目的
`requestAnimationFrame` 旨在提高动画的效率和性能，避免过高的 CPU 使用率，并确保动画与浏览器的刷新率同步。它是构建高效、流畅动画的推荐方法。

### 用法
`requestAnimationFrame` 方法的基本语法如下：

```javascript
let requestId = requestAnimationFrame(callback);
```

- **callback**：一个函数，表示在下一个重绘之前要执行的代码。
- **返回值**：此方法返回一个整数 ID，用于唯一标识该动画帧请求，可以用于取消帧请求。

### 详细说明
1. **优化性能**：使用 `requestAnimationFrame` 可以让浏览器决定最佳的时间点来执行动画，从而避免动画卡顿。
2. **自动调整刷新率**：该方法会在浏览器的刷新周期内运行，通常是每秒 60 次，确保动画的流畅性。
3. **支持取消**：通过 `cancelAnimationFrame(requestId)` 可以取消之前的请求，避免不必要的计算和性能损耗。

## 示例
### 基本用法

```javascript
let start = null;

function animate(timestamp) {
    if (!start) start = timestamp;
    const progress = timestamp - start;

    // 更新动画状态
    // 例如：更新元素位置
    document.getElementById("myElement").style.transform = `translateX(${progress / 10}px)`;

    // 继续请求下一帧
    if (progress < 2000) { // 动画持续时间为 2000 毫秒
        requestAnimationFrame(animate);
    }
}

// 启动动画
requestAnimationFrame(animate);
```

## 解释
- **常见陷阱**：
    - 不要在动画回调中使用 `setTimeout` 或 `setInterval`，因为它们会打乱与浏览器重绘的同步。
    - 确保在不需要时取消动画帧请求，以避免不必要的资源消耗。

- **注意事项**：
    - 如果用户切换到其他标签页，`requestAnimationFrame` 会自动暂停，以节省资源。
    - 动画的流畅度可能会受到设备性能和浏览器实现的影响。

## 一句话总结
`requestAnimationFrame` 是提高 JavaScript 动画性能的关键方法，通过在浏览器的重绘周期内优化动画调用，确保流畅的用户体验。