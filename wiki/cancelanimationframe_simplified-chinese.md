<!--
Meta Description: # cancelAnimationFrame：JavaScript 动画控制的关键方法 ## 摘要 `cancelAnimationFrame` 是一个用于取消通过 `requestAnimationFrame` 方法所注册的动画帧请求的 JavaScript 方法。它帮助开发者在需要时停止动画的执...
Meta Keywords: cancelanimationframe, requestanimationframe, requestid, javascript, animate
-->

# cancelAnimationFrame：JavaScript 动画控制的关键方法

## 摘要
`cancelAnimationFrame` 是一个用于取消通过 `requestAnimationFrame` 方法所注册的动画帧请求的 JavaScript 方法。它帮助开发者在需要时停止动画的执行，优化性能和资源使用。

## 文档
### 目的
`cancelAnimationFrame` 方法用于取消一个先前通过 `requestAnimationFrame` 创建的动画帧请求。它接受一个参数，即请求的 ID，这个 ID 是在调用 `requestAnimationFrame` 时返回的。

### 用法
```javascript
let requestId = requestAnimationFrame(callback);
cancelAnimationFrame(requestId);
```
- **参数**：
  - `requestId`：由 `requestAnimationFrame` 返回的整数 ID，表示要取消的动画请求。

- **返回值**：该方法没有返回值。

### 详细信息
- `cancelAnimationFrame` 是与 `requestAnimationFrame` 配对使用的，使用它可以有效地管理动画的生命周期。
- 当你需要停止一个即将执行的动画时，调用 `cancelAnimationFrame` 可以避免不必要的计算和渲染，从而提升性能。
- 如果你传入一个无效的 ID，`cancelAnimationFrame` 不会产生错误，但也不会有任何效果。

## 示例
### 基本用法示例
```javascript
let requestId;

function animate() {
    // 动画代码
    console.log("Animating...");

    // 请求下一个动画帧
    requestId = requestAnimationFrame(animate);
}

// 启动动画
animate();

// 在某些条件下取消动画
setTimeout(() => {
    cancelAnimationFrame(requestId);
    console.log("Animation cancelled.");
}, 2000);
```

## 解释
### 常见陷阱
- **无效的 ID**：如果调用 `cancelAnimationFrame` 时传入的 ID 不存在，函数不会报错，但也不会取消任何正在进行的请求。
- **未保存请求 ID**：如果在调用 `requestAnimationFrame` 后没有保存返回的 ID，就无法正确地取消动画。
- **多次请求**：在同一帧中多次调用 `requestAnimationFrame` 将返回多个 ID，如果只想取消其中一个，需确保保存所有 ID。

### 附加说明
- `cancelAnimationFrame` 是浏览器提供的 API，效率高且适用于大多数现代浏览器。
- 动画的频率应与浏览器的刷新率保持一致，通常为 60 帧每秒，这样可以获得平滑的视觉效果。

## 一句话总结
`cancelAnimationFrame` 是一个在 JavaScript 中用于取消已注册动画帧请求的有效方法，帮助开发者优化动画性能。