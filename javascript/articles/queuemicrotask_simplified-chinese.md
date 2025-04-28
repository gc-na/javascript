<!--
Meta Description: # queueMicrotask：JavaScript 中的微任务队列 ## 概述 `queueMicrotask` 是 JavaScript 中的一个方法，用于将一个微任务添加到微任务队列中。微任务是在当前事件循环的尾部执行的任务，通常用于处理 Promise 的回调。 ## 文档 ### 目的 ...
Meta Keywords: queuemicrotask, promise, console, log, javascript
-->

# queueMicrotask：JavaScript 中的微任务队列

## 概述
`queueMicrotask` 是 JavaScript 中的一个方法，用于将一个微任务添加到微任务队列中。微任务是在当前事件循环的尾部执行的任务，通常用于处理 Promise 的回调。

## 文档
### 目的
`queueMicrotask` 的主要目的是在当前执行的 JavaScript 代码完成后，尽快执行指定的回调函数。与 `setTimeout` 和 `setImmediate` 不同，微任务优先级更高，因此适合用于处理需要立即完成的操作，例如更新视图或处理 Promise。

### 用法
```javascript
queueMicrotask(callback);
```

- **参数**：
  - `callback`：一个函数，表示要执行的微任务。

- **返回值**：
  - 无返回值。

### 详细说明
- 微任务队列在任务队列之前执行，所有微任务都会在当前宏任务结束后立即执行，直到队列为空。
- `queueMicrotask` 不会影响当前任务的执行顺序，它会在当前任务完成后立即执行。

## 示例
### 基本用法
```javascript
console.log("开始");

queueMicrotask(() => {
  console.log("微任务执行");
});

console.log("结束");
```
**输出**：
```
开始
结束
微任务执行
```

### 结合 Promise 使用
```javascript
new Promise((resolve) => {
  console.log("Promise 开始");
  resolve();
}).then(() => {
  console.log("Promise then");
  queueMicrotask(() => {
    console.log("微任务中执行");
  });
});

console.log("Promise 结束");
```
**输出**：
```
Promise 开始
Promise 结束
Promise then
微任务中执行
```

## 说明
- **与 setTimeout 的区别**：`queueMicrotask` 的任务会在当前执行栈清空后立即执行，而 `setTimeout` 指定的回调会在最少等待 0 毫秒后执行，优先级较低。
- **常见陷阱**：如果在微任务中调用 `queueMicrotask`，可能会导致无限循环，需谨慎使用。
- **性能考虑**：过多的微任务可能导致性能问题，因此应合理安排微任务的使用。

## 一句话总结
`queueMicrotask` 是一个用于将微任务添加到微任务队列中的方法，能在当前任务完成后立即执行指定的回调函数。