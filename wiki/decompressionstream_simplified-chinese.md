<!--
Meta Description: # DecompressionStream：JavaScript 中的解压缩流 ## 概述 `DecompressionStream` 是一种用于处理压缩数据的 JavaScript 接口，允许开发者在 Web 应用程序中解压缩数据流。该接口通过将压缩数据流转换为可读数据流，简化了处理和使用压缩格式...
Meta Keywords: decompressionstream, readablestream, const, javascript, new
-->

# DecompressionStream：JavaScript 中的解压缩流

## 概述
`DecompressionStream` 是一种用于处理压缩数据的 JavaScript 接口，允许开发者在 Web 应用程序中解压缩数据流。该接口通过将压缩数据流转换为可读数据流，简化了处理和使用压缩格式（如 Gzip、Deflate）的过程。

## 文档
### 目的
`DecompressionStream` 的主要目的是提供一种有效的方法来解压缩传入的二进制数据流，使得开发者可以方便地在 JavaScript 环境中处理压缩内容。

### 使用方式
要使用 `DecompressionStream`，开发者需要创建一个新的 `DecompressionStream` 实例，并将其应用于输入的压缩数据流。以下是基本的使用步骤：

1. 创建一个 `ReadableStream` 用于接收压缩数据。
2. 创建一个 `DecompressionStream` 实例，指定要解压缩的格式。
3. 将 `DecompressionStream` 作为管道连接到可读流。
4. 处理解压缩后的数据流。

### 详细信息
- **构造函数**: `new DecompressionStream(format)`
  - `format`：可选参数，指定解压缩的格式（如 `"gzip"` 或 `"deflate"`）。
  
- **返回值**：返回一个 `ReadableStream`，可以通过该流读取解压缩后的数据。

- **浏览器支持**：确保目标浏览器支持 `DecompressionStream`，可通过特性检测来验证。

## 示例
### 示例 1：基本解压缩用法
```javascript
const compressedStream = new ReadableStream({
    // 这里可以定义一个生产者来产生压缩数据流
});

const decompressionStream = new DecompressionStream('gzip');

const readableStream = compressedStream.pipeThrough(decompressionStream);

const reader = readableStream.getReader();
reader.read().then(({ done, value }) => {
    if (!done) {
        console.log(new TextDecoder().decode(value)); // 输出解压缩后的数据
    }
});
```

### 示例 2：从网络获取并解压缩数据
```javascript
fetch('data.txt.gz')
    .then(response => response.body)
    .then(compressedStream => {
        const decompressionStream = new DecompressionStream('gzip');
        const readableStream = compressedStream.pipeThrough(decompressionStream);
        
        const reader = readableStream.getReader();
        return reader.read();
    })
    .then(({ done, value }) => {
        if (!done) {
            console.log(new TextDecoder().decode(value)); // 输出解压缩后的数据
        }
    });
```

## 说明
- **常见问题**：
  - 确保输入流确实是压缩格式的，否则 `DecompressionStream` 可能无法正确处理数据。
  - 对于较大的数据流，最好使用异步处理来避免阻塞主线程。

- **注意事项**：
  - 不同的浏览器对 `DecompressionStream` 的支持程度可能不同，建议在使用前进行测试。
  - 当处理多个解压缩流时，确保正确管理流的生命周期，以避免内存泄漏。

## 一句话总结
`DecompressionStream` 是 JavaScript 中用于解压缩数据流的接口，可以有效地处理压缩格式的数据。