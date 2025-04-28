<!--
Meta Description: # JavaScript 中的 onrejectionhandled 事件详解 ## 概述 `onrejectionhandled` 是 JavaScript 中的一个事件处理器，用于处理 Promise 被拒绝后，用户自定义的拒绝处理程序的执行。此事件在 Promise 被拒绝且相应的拒绝处理程序...
Meta Keywords: promise, onrejectionhandled, javascript, event, window
-->

# JavaScript 中的 onrejectionhandled 事件详解

## 概述
`onrejectionhandled` 是 JavaScript 中的一个事件处理器，用于处理 Promise 被拒绝后，用户自定义的拒绝处理程序的执行。此事件在 Promise 被拒绝且相应的拒绝处理程序被调用时触发，能够帮助开发者跟踪未处理的 Promise 拒绝情况。

## 文档
### 目的
`onrejectionhandled` 事件旨在提供一种机制，允许开发者捕捉 Promise 拒绝的处理过程，从而增强错误处理能力。

### 用法
要使用 `onrejectionhandled`，您需要将其分配给 `window` 对象。该事件在 Promise 的拒绝处理程序被调用时触发。您可以通过以下方式设置事件处理器：

```javascript
window.onrejectionhandled = function(event) {
    console.log('Promise rejection handled:', event.promise);
};
```

### 细节
- `onrejectionhandled` 事件的处理器接收一个事件对象，该对象包含与被拒绝的 Promise 相关的信息。
- 该事件在 Promise 拒绝并且其拒绝处理程序被调用时触发，而不是在 Promise 被拒绝时。
- 如果 Promise 的拒绝未被处理，它将触发 `unhandledrejection` 事件。

## 示例
以下是 `onrejectionhandled` 的基本使用示例：

```javascript
window.onrejectionhandled = function(event) {
    console.log('Handled rejection:', event.promise);
};

const myPromise = new Promise((resolve, reject) => {
    reject('Something went wrong');
});

// 添加拒绝处理程序
myPromise.catch(error => {
    console.log('Error caught:', error);
});
```

在这个例子中，当 `myPromise` 被拒绝时，`onrejectionhandled` 会捕捉到处理程序的执行。

## 说明
- **常见陷阱**：如果没有为 Promise 添加拒绝处理程序，`onrejectionhandled` 将不会被触发。
- **注意事项**：确保您的 Promise 始终有相应的拒绝处理程序，以避免未处理的拒绝情况导致的潜在错误。
- `onrejectionhandled` 事件仅对在 Promise 处理程序中调用的拒绝有效，不会对其他异步操作产生影响。

## 一句话总结
`onrejectionhandled` 事件允许开发者跟踪 Promise 拒绝的处理过程，从而增强错误处理能力。