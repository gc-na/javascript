<!--
Meta Description: # ReadableStreamDefaultReader：JavaScript 中的可讀流默認讀取器 ## 概述 `ReadableStreamDefaultReader` 是 JavaScript 中一個用於從可讀流 (`ReadableStream`) 中讀取數據的接口。它提供了一種方法來異步...
Meta Keywords: controller, readablestream, readablestreamdefaultreader, reader, javascript
-->

# ReadableStreamDefaultReader：JavaScript 中的可讀流默認讀取器

## 概述
`ReadableStreamDefaultReader` 是 JavaScript 中一個用於從可讀流 (`ReadableStream`) 中讀取數據的接口。它提供了一種方法來異步讀取流中的數據塊，使開發者能夠輕鬆處理流式數據。

## 文檔
### 目的
`ReadableStreamDefaultReader` 的主要目的是讓開發者以異步方式從可讀流中讀取數據。它是與可讀流一起使用的，允許用戶逐塊讀取數據，這對於處理大型數據集或流式數據特別有用。

### 使用方式
要使用 `ReadableStreamDefaultReader`，首先需要創建一個可讀流，然後使用 `getReader()` 方法獲取讀取器。該讀取器提供 `read()` 方法來異步讀取數據，並返回一個包含數據和完成狀態的 Promise。

```javascript
const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello, ');
    controller.enqueue('world!');
    controller.close();
  }
});

const reader = readableStream.getReader();
```

### 詳細說明
- **方法**
  - `read()`：從流中讀取下一個數據塊，返回一個 Promise，該 Promise 解析為一個對象，包含兩個屬性：`value`（讀取的數據）和 `done`（指示是否已經到達流的結尾）。
  - `releaseLock()`：釋放這個讀取器對流的鎖，允許其他讀取器訪問流。

- **屬性**
  - `closed`：返回一個 Promise，它在流關閉時解析。

## 範例
以下是一些基本的用法示例：

### 示例 1：基本讀取
```javascript
const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello, ');
    controller.enqueue('world!');
    controller.close();
  }
});

const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  console.log(done);  // false
  console.log(value); // "Hello, "
});
```

### 示例 2：讀取整個流
```javascript
async function readStream(reader) {
  let result;
  while (!(result = await reader.read()).done) {
    console.log(result.value);
  }
}

readStream(reader);
```

## 解釋
在使用 `ReadableStreamDefaultReader` 時，有一些常見的陷阱和注意事項：
- 確保使用 `releaseLock()` 釋放讀取器的鎖，以便在不再需要時能夠正確地釋放資源。
- 在讀取流時，注意流的狀態，確保不會在流已經完成時再次調用 `read()` 方法。
- 異步讀取操作可能會涉及多次 Promise 的解析，因此要注意錯誤處理。

## 一句總結
`ReadableStreamDefaultReader` 是一個強大的工具，可以幫助開發者以異步方式從可讀流中逐塊讀取數據。