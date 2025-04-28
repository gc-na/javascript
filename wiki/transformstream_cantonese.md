<!--
Meta Description: # TransformStream：JavaScript 中的數據轉換流 ## Synopsis TransformStream 係一個用於處理可讀和可寫流之間數據轉換的 API，方便開發者創建自定義數據處理邏輯。 ## Documentation TransformStream 係 Web Str...
Meta Keywords: transformstream, writer, const, value, reader
-->

# TransformStream：JavaScript 中的數據轉換流

## Synopsis
TransformStream 係一個用於處理可讀和可寫流之間數據轉換的 API，方便開發者創建自定義數據處理邏輯。

## Documentation
TransformStream 係 Web Streams API 嘅一部分，佢的主要目的是允許開發者對流中的數據進行轉換。呢個 API 可以用於實現數據的壓縮、加密、格式轉換等功能。

### 基本結構
TransformStream 由兩個主要組件組成：
- **可讀流 (ReadableStream)**: 用於讀取轉換後的數據。
- **可寫流 (WritableStream)**: 用於寫入需要轉換的原始數據。

### 使用方法
要創建一個 TransformStream，你需要提供一個轉換函數，該函數會在寫入數據時被調用。示例代碼如下：

```javascript
const { TransformStream } = require('stream/web');

const transformStream = new TransformStream({
  transform(chunk, controller) {
    // 對每個塊進行轉換
    const transformedChunk = chunk.toUpperCase();
    controller.enqueue(transformedChunk);
  }
});

// 使用可寫流寫入數據
const writer = transformStream.writable.getWriter();
writer.write('hello');
writer.write('world');
writer.close();

// 使用可讀流讀取轉換後的數據
const reader = transformStream.readable.getReader();
reader.read().then(({ value, done }) => {
  console.log(value); // 輸出: 'HELLO'
});
```

## Examples
### 基本轉換示例
```javascript
const transformStream = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk * 2); // 將每個數字乘以 2
  }
});

const writer = transformStream.writable.getWriter();
writer.write(1);
writer.write(2);
writer.write(3);
writer.close();

const reader = transformStream.readable.getReader();
reader.read().then(({ value }) => console.log(value)); // 輸出: 2
reader.read().then(({ value }) => console.log(value)); // 輸出: 4
```

### 字符串轉換示例
```javascript
const stringTransform = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk.toLowerCase()); // 將字符串轉為小寫
  }
});

const writer = stringTransform.writable.getWriter();
writer.write('HELLO');
writer.write('WORLD');
writer.close();

const reader = stringTransform.readable.getReader();
reader.read().then(({ value }) => console.log(value)); // 輸出: hello
reader.read().then(({ value }) => console.log(value)); // 輸出: world
```

## Explanation
### 常見問題
1. **流的結束**: 確保在寫入完所有數據後調用 `close()` 方法，否則可讀流將無法正確結束。
2. **控制器的使用**: 使用控制器的 `enqueue` 方法來插入轉換後的數據，這樣才能保證數據正確流動。
3. **轉換函數的性能**: 在轉換函數中執行高性能計算可能會影響流的性能，應謹慎設計轉換邏輯。

## One Line Summary
TransformStream 係一個方便的 JavaScript API，用於在可讀和可寫流之間進行數據轉換。