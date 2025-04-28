<!--
Meta Description: # AbortSignal: JavaScript 中的中止信号 ## 概述 `AbortSignal` 是 JavaScript 中用于取消异步操作的一种机制，特别是在进行网络请求或其他长时间运行的任务时。它通过与 `AbortController` 结合使用，允许开发者优雅地终止这些操作。 ##...
Meta Keywords: abortsignal, javascript, controller, signal, abortcontroller
-->

# AbortSignal: JavaScript 中的中止信号

## 概述
`AbortSignal` 是 JavaScript 中用于取消异步操作的一种机制，特别是在进行网络请求或其他长时间运行的任务时。它通过与 `AbortController` 结合使用，允许开发者优雅地终止这些操作。

## 文档
### 目的
`AbortSignal` 旨在为异步操作提供一种中止信号，使开发者能够控制何时取消这些操作，避免不必要的资源消耗。

### 使用方法
1. **创建 AbortController 实例**：
   ```javascript
   const controller = new AbortController();
   ```

2. **获取 AbortSignal**：
   ```javascript
   const signal = controller.signal;
   ```

3. **将信号传递给异步操作**：
   ```javascript
   fetch('https://example.com/api', { signal })
     .then(response => {
       // 处理响应
     })
     .catch(err => {
       if (err.name === 'AbortError') {
         console.log('请求被中止');
       }
     });
   ```

4. **触发中止操作**：
   ```javascript
   controller.abort();
   ```

### 详情
`AbortSignal` 对象代表一个中止信号并且可以被多个异步操作共享。每当 `AbortController` 的 `abort()` 方法被调用时，所有使用该信号的操作都会立即中止，并抛出一个 `AbortError`。这使得清理和管理异步操作更加高效。

## 示例
### 示例 1：基础用法
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://example.com/api', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('请求被中止');
    }
  });

// 1秒后中止请求
setTimeout(() => {
  controller.abort();
}, 1000);
```

### 示例 2：与 Promise 一起使用
```javascript
function fetchData(signal) {
  return new Promise((resolve, reject) => {
    // 模拟异步操作
    const timeoutId = setTimeout(() => {
      resolve('数据加载完成');
    }, 3000);

    signal.addEventListener('abort', () => {
      clearTimeout(timeoutId);
      reject(new Error('操作被中止'));
    });
  });
}

const controller = new AbortController();
fetchData(controller.signal)
  .then(data => console.log(data))
  .catch(err => console.error(err.message));

// 1秒后中止操作
setTimeout(() => {
  controller.abort();
}, 1000);
```

## 说明
- **常见陷阱**：在使用 `AbortSignal` 时，确保在调用 `abort()` 方法之前没有其他异步操作已经完成，否则会导致不必要的错误处理。
- **支持性**：`AbortSignal` 在现代浏览器中广泛支持，但在某些旧版浏览器中可能不兼容，建议在使用时检查支持性。
- **多个操作**：可以将同一个 `AbortSignal` 传递给多个异步操作，所有这些操作都能被同一个控制器中止。

## 一句话总结
`AbortSignal` 是 JavaScript 中用于控制异步操作的中止机制，提供了一种方便的方式来管理和取消请求。