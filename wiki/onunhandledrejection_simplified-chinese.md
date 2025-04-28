<!--
Meta Description: # JavaScript 的 onunhandledrejection 事件详解 ## 概述 `onunhandledrejection` 是一个全局事件处理器，用于捕获在 JavaScript Promise 中未处理的拒绝（rejection）情况。它允许开发者处理 Promise 拒绝的错误，...
Meta Keywords: onunhandledrejection, promise, event, javascript, catch
-->

# JavaScript 的 onunhandledrejection 事件详解

## 概述
`onunhandledrejection` 是一个全局事件处理器，用于捕获在 JavaScript Promise 中未处理的拒绝（rejection）情况。它允许开发者处理 Promise 拒绝的错误，提供了对异步代码的更好控制和错误监测能力。

## 文档
`onunhandledrejection` 事件在 Promise 被拒绝但没有被 `.catch()` 或 `try/catch` 语句捕获时触发。事件对象包含有关拒绝的详细信息，可以用来记录错误或执行其他必要的操作。

### 用法
你可以通过将一个函数赋值给 `window.onunhandledrejection` 来注册事件处理器。例如：

```javascript
window.onunhandledrejection = function(event) {
    console.warn('未处理的拒绝:', event.reason);
};
```

### 事件对象
事件对象 `event` 包含以下属性：
- `reason`: 拒绝的原因，通常是一个错误对象。
- `promise`: 相关的 Promise 对象。

## 示例
### 基本用法
下面是一个简单的示例，展示如何使用 `onunhandledrejection` 捕获未处理的 Promise 拒绝：

```javascript
// 注册未处理拒绝事件处理器
window.onunhandledrejection = function(event) {
    console.warn('未处理的拒绝:', event.reason);
};

// 创建一个未处理的 Promise 拒绝
const promise = new Promise((resolve, reject) => {
    reject(new Error('发生了一个错误！'));
});

// 由于没有使用 .catch()，该拒绝将触发 onunhandledrejection 事件
```

### 结合 try/catch 使用
在某些情况下，你可能希望结合 `try/catch` 与 `onunhandledrejection` 使用，以确保所有错误都被捕获：

```javascript
window.onunhandledrejection = function(event) {
    console.warn('未处理的拒绝:', event.reason);
};

async function asyncFunction() {
    throw new Error('异步错误！');
}

asyncFunction().catch(err => {
    console.error('处理的错误:', err);
});
```

## 解释
### 常见陷阱
1. **未捕获的 Promise 拒绝**：在未处理的情况下，Promise 拒绝不会停止代码执行，但可能会导致后续逻辑错误。
2. **事件处理器未注册**：如果 `onunhandledrejection` 事件处理器未注册，未处理的拒绝将不会被捕获，可能导致调试困难。

### 注意事项
- 使用 `onunhandledrejection` 事件处理器可以提高应用程序的健壮性，建议在应用程序的入口文件中注册。
- 在生产环境中，记录未处理的拒绝信息对于监控和调试异步操作的错误非常重要。

## 一句话总结
`onunhandledrejection` 事件用于捕获 JavaScript 中未处理的 Promise 拒绝，帮助开发者更好地管理异步错误。