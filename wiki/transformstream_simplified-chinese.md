<!--
Meta Description: # TransformStream：JavaScript 中的数据转换流 ## 概述 TransformStream 是一种在 JavaScript 中用于处理数据流的接口，允许你以流的方式转换数据。它通常用于处理大数据集，例如文件流、网络请求等，能够在传输过程中对数据进行实时转换。 ## 文档 #...
Meta Keywords: transformstream, const, javascript, writer, transform
-->

# TransformStream：JavaScript 中的数据转换流

## 概述
TransformStream 是一种在 JavaScript 中用于处理数据流的接口，允许你以流的方式转换数据。它通常用于处理大数据集，例如文件流、网络请求等，能够在传输过程中对数据进行实时转换。

## 文档
### 目的
TransformStream 的主要目的是提供一种高效的方式来处理和转换数据流。它支持可读和可写的流，可以在数据从一个源流被读取到目标流的过程中进行转换处理。

### 用法
TransformStream 可以通过以下构造函数创建：

```javascript
const transformStream = new TransformStream(transformer);
```

其中 `transformer` 是一个包含 `start` 和 `transform` 方法的对象：

- **start**：在流开始时调用，可以用于初始化状态。
- **transform**：每当有数据传入时调用，可以处理输入数据并将结果输出到可写流。

### 细节
- TransformStream 继承自 WritableStream 和 ReadableStream。
- 你可以使用 `readable` 和 `writable` 属性来访问流的可读和可写部分。
- 数据是以块的形式处理的，适合处理渐进式的数据流。

## 示例
以下是一个简单的使用示例，将输入数据转换为大写字母：

```javascript
const { TransformStream } = require('stream/web');

const uppercaseTransformer = {
  transform(chunk, controller) {
    controller.enqueue(chunk.toUpperCase());
  }
};

const transformStream = new TransformStream(uppercaseTransformer);

const writer = transformStream.writable.getWriter();
const reader = transformStream.readable.getReader();

writer.write('hello');
writer.write(' world');
writer.close();

async function readStream() {
  let result;
  while (!(result = await reader.read()).done) {
    console.log(result.value); // 输出: 'HELLO' 和 ' WORLD'
  }
}

readStream();
```

## 解释
- **常见陷阱**：确保在使用 `writer.close()` 后，不再向流写入数据，否则会抛出错误。
- **注意事项**：TransformStream 适合处理增量数据，避免一次性处理大量数据以防内存溢出。
- **兼容性**：TransformStream 是现代浏览器和 Node.js 的一部分，确保在使用时检查环境的兼容性。

## 一句话总结
TransformStream 是 JavaScript 中用于高效转换数据流的接口，支持实时数据处理和转换。