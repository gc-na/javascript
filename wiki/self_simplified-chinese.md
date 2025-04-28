<!--
Meta Description: # JavaScript 中的 "self"：理解上下文与作用域 ## 概述 在 JavaScript 中，`self` 是一个全局对象的引用，通常用于指向全局上下文中的窗口对象，尤其在 Web 开发中。它允许开发者访问全局作用域中的变量和函数。 ## 文档 ### 目的 `self` 提供了一个指...
Meta Keywords: self, worker, web, window, javascript
-->

# JavaScript 中的 "self"：理解上下文与作用域

## 概述
在 JavaScript 中，`self` 是一个全局对象的引用，通常用于指向全局上下文中的窗口对象，尤其在 Web 开发中。它允许开发者访问全局作用域中的变量和函数。

## 文档
### 目的
`self` 提供了一个指向全局上下文的引用，尤其是在 Web 浏览器环境中，`self` 通常与 `window` 对象等价。它可以在不同的上下文中使用，确保开发者能够访问全局变量。

### 用法
`self` 主要用于以下场景：
- 在 Web Worker 中，`self` 是指向 Worker 自身的对象。
- 在全局环境中，`self` 是对 `window` 对象的引用。

### 细节
- 在浏览器环境中，`self` 和 `window` 是等价的，可以互换使用。
- 在 Web Worker 中，`self` 不再指向 `window`，而是指向 Worker 的全局上下文。

## 示例
以下是 `self` 的基本用法示例：

1. 在浏览器环境中：
   ```javascript
   console.log(self === window); // 输出: true
   console.log(self.document.title); // 输出当前文档的标题
   ```

2. 在 Web Worker 中：
   ```javascript
   // worker.js
   self.onmessage = function (e) {
       console.log('Worker received message: ', e.data);
       self.postMessage('Hello from Worker!');
   };
   ```

## 解释
- **常见陷阱**：在使用 `self` 时，开发者可能会混淆它与其他上下文的作用。特别是在使用函数时，`this` 的上下文可能会变化，因此使用 `self` 可以避免上下文丢失的问题。
- **注意事项**：在非浏览器环境（如 Node.js）中，`self` 并不被定义，因此应谨慎使用。

## 一句话总结
`self` 是一个指向全局上下文的引用，通常用于访问全局变量和函数，尤其在 Web 开发中。