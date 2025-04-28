<!--
Meta Description: # ReadableStream：JavaScript 中的可读流 ## 概述 `ReadableStream` 是 JavaScript 中用于处理流数据的接口，允许开发者以流的形式读取数据，尤其适用于处理大文件或实时数据，以提高性能和用户体验。 ## 文档 ### 目的 `ReadableStr...
Meta Keywords: readablestream, controller, reader, value, javascript
-->

# ReadableStream：JavaScript 中的可读流

## 概述
`ReadableStream` 是 JavaScript 中用于处理流数据的接口，允许开发者以流的形式读取数据，尤其适用于处理大文件或实时数据，以提高性能和用户体验。

## 文档
### 目的
`ReadableStream` 的主要目的是提供一种方法来异步读取数据流。它允许开发者逐块读取数据，而不是一次性将整个数据集加载到内存中，从而节省资源并提高效率。

### 用法
`ReadableStream` 的基本构造函数如下：

```javascript
const stream = new ReadableStream({
  start(controller) {
    // 初始化代码
  },
  pull(controller) {
    // 被调用以请求更多数据
  },
  cancel() {
    // 取消流时的清理代码
  }
});
```

- **start(controller)**: 在流开始时调用，允许开发者在流的初始化阶段填充数据。
- **pull(controller)**: 当流的消费者请求更多数据时调用，允许开发者提供更多数据。
- **cancel()**: 当流被取消时调用，用于进行清理操作。

### 详细信息
`ReadableStream` 可以与其他 Web API（如 Fetch API）结合使用，以处理从服务器接收的数据流。它可以通过 `getReader()` 方法获取一个读取器，读取器允许逐块地读取流数据。

```javascript
const reader = stream.getReader();
reader.read().then(({ done, value }) => {
  if (!done) {
    console.log(value); // 处理读取到的数据
  }
});
```

## 示例
### 基本使用示例
以下是一个简单的示例，展示如何创建和读取 `ReadableStream`：

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello, ');
    controller.enqueue('World!');
    controller.close();
  }
});

const reader = stream.getReader();

reader.read().then(({ done, value }) => {
  console.log(value); // 输出: Hello,
});

reader.read().then(({ done, value }) => {
  console.log(value); // 输出: World!
});
```

### 从 Fetch API 读取流
使用 `ReadableStream` 读取 Fetch 请求的响应数据：

```javascript
fetch('https://example.com/data')
  .then(response => {
    const reader = response.body.getReader();
    return reader.read();
  })
  .then(({ done, value }) => {
    console.log(new TextDecoder().decode(value));
  });
```

## 解释
在使用 `ReadableStream` 时，开发者需要注意以下几点：
- 确保在 `start` 方法中正确地调用 `controller.enqueue()` 来填充数据。
- 在流结束时，使用 `controller.close()` 关闭流。
- 注意流的消费方式，调用 `reader.read()` 会返回一个 Promise，且需要处理 `done` 状态，确定是否还有更多数据可读取。
- 处理流时，确保适当的错误处理，以避免未捕获的异常。

## 一句话总结
`ReadableStream` 是一个 JavaScript 接口，用于高效地异步读取流数据，适合处理大文件和实时数据。