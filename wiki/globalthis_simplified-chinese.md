<!--
Meta Description: # globalThis：JavaScript中的全局对象 ## 概述 `globalThis` 是一个全局对象，在JavaScript中提供了一种统一的方式来访问全局作用域。它在不同的执行环境（如浏览器、Node.js）中均可使用，解决了不同环境中全局对象名称不一致的问题。 ## 文档 ### 目...
Meta Keywords: globalthis, global, console, log, javascript
-->

# globalThis：JavaScript中的全局对象

## 概述
`globalThis` 是一个全局对象，在JavaScript中提供了一种统一的方式来访问全局作用域。它在不同的执行环境（如浏览器、Node.js）中均可使用，解决了不同环境中全局对象名称不一致的问题。

## 文档
### 目的
`globalThis` 的主要目的是提供一个标准化的方式来访问全局对象，不论你是在浏览器环境还是Node.js环境中工作。它减少了对全局对象（如 `window` 或 `global`）的直接引用，增强了代码的可移植性。

### 用法
使用 `globalThis` 时，你可以直接引用它来访问全局范围内的变量和函数。如果你在浏览器控制台中输入 `globalThis`，将返回全局 `window` 对象；而在Node.js中，它将返回 `global` 对象。

```javascript
// 在浏览器中
console.log(globalThis === window); // 输出: true

// 在Node.js中
console.log(globalThis === global); // 输出: true
```

### 细节
- `globalThis` 是 ECMAScript 2020 (ES11) 中引入的功能，因此在较旧的JavaScript环境中可能不被支持。
- 可以通过 `globalThis` 访问或设置全局变量，例如：

```javascript
globalThis.myGlobalVar = 'Hello, World!';
console.log(myGlobalVar); // 输出: Hello, World!
```

## 示例
以下是一些 `globalThis` 的基本用法示例：

1. **访问全局变量**：
   ```javascript
   globalThis.foo = 'bar';
   console.log(globalThis.foo); // 输出: bar
   ```

2. **定义全局函数**：
   ```javascript
   globalThis.myFunction = function() {
       console.log('This is a global function.');
   };
   myFunction(); // 输出: This is a global function.
   ```

3. **在不同环境中的一致性**：
   ```javascript
   // 在浏览器中
   console.log(globalThis === window); // 输出: true

   // 在Node.js中
   console.log(globalThis === global); // 输出: true
   ```

## 说明
- **常见问题**：在某些情况下，使用 `globalThis` 可能会引起混淆，特别是当开发者习惯于使用特定环境的全局对象（如 `window` 或 `global`）。因此，在编写可移植的代码时，应优先考虑使用 `globalThis`。
- **兼容性**：确保你的运行环境支持 ES2020，或者使用 Babel 等工具进行转译，以支持早期版本的 JavaScript 环境。
- **命名冲突**：与其他全局变量或函数名称可能会发生冲突，因此在定义新的全局变量或函数时，请谨慎选择名称。

## 一句话总结
`globalThis` 是一种访问JavaScript全局对象的标准方法，适用于所有执行环境。