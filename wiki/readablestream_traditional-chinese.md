<!--
Meta Description: # ReadableStream：JavaScript 中的可讀串流 ## 概述 `ReadableStream` 是一種 JavaScript API，允許開發者以流的方式處理數據，特別適用於處理大型數據集或異步數據。它使得在處理數據時可以更有效地管理內存並提高性能。 ## 文件說明 `Reada...
Meta Keywords: readablestream, controller, javascript, const, reader
-->

# ReadableStream：JavaScript 中的可讀串流

## 概述
`ReadableStream` 是一種 JavaScript API，允許開發者以流的方式處理數據，特別適用於處理大型數據集或異步數據。它使得在處理數據時可以更有效地管理內存並提高性能。

## 文件說明
`ReadableStream` 提供了一種可讀的數據流，讓你可以從各種來源（如網絡請求、文件系統等）讀取數據，而不需要一次性加載所有數據。這對於處理較大數據集時特別有用，可以在數據可用時逐步讀取，降低內存消耗。

### 目的
`ReadableStream` 旨在改善數據處理的靈活性和效率，尤其是在需要逐步獲取數據的場景中。

### 用法
要創建一個 `ReadableStream`，你可以使用以下語法：

```javascript
const stream = new ReadableStream({
  start(controller) {
    // 初始化代碼
  },
  pull(controller) {
    // 每當需要更多數據時調用
  },
  cancel() {
    // 可選的取消處理
  }
});
```

### 屬性和方法
- **start(controller)**: 初始化流，通常用來設置初始狀態。
- **pull(controller)**: 當消費者需要更多數據時調用，可以在這裡填充數據。
- **cancel()**: 在流被取消時調用，通常用於清理資源。

## 範例
以下是一些基本的 `ReadableStream` 使用範例：

### 範例 1：簡單的可讀串流
```javascript
const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello');
    controller.enqueue('World');
    controller.close();
  }
});

const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  console.log(value); // 輸出：Hello
});
```

### 範例 2：從 API 讀取數據
```javascript
async function fetchStreamData(url) {
  const response = await fetch(url);
  const readableStream = response.body;

  const reader = readableStream.getReader();
  let result;
  while (!(result = await reader.read()).done) {
    console.log(new TextDecoder().decode(result.value));
  }
}

fetchStreamData('https://api.example.com/data');
```

## 解釋
在使用 `ReadableStream` 時，開發者需要注意以下幾點：

1. **異步行為**: `ReadableStream` 的讀取操作是異步的，這意味著在處理數據時需要使用 `Promise` 或 `async/await` 來管理流程。
2. **流的取消**: 如果不再需要數據，應使用 `cancel()` 方法來中止流，這樣可以釋放資源並避免不必要的計算。
3. **內存管理**: 使用流可以顯著降低內存消耗，尤其是在處理大量數據或持續數據流時。

## 一句總結
`ReadableStream` 是 JavaScript 中一種有效的數據處理方式，允許開發者以流的形式逐步讀取和管理數據。