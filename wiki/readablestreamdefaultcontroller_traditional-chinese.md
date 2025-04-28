<!--
Meta Description: # ReadableStreamDefaultController：JavaScript 中的可讀流控制器 ## 摘要 `ReadableStreamDefaultController` 是 JavaScript 中一個重要的接口，專門用於控制可讀流的行為，允許開發者管理流的生成、取消和狀態。 ##...
Meta Keywords: controller, readablestreamdefaultcontroller, readablestream, javascript, enqueue
-->

# ReadableStreamDefaultController：JavaScript 中的可讀流控制器

## 摘要
`ReadableStreamDefaultController` 是 JavaScript 中一個重要的接口，專門用於控制可讀流的行為，允許開發者管理流的生成、取消和狀態。

## 文檔
`ReadableStreamDefaultController` 是 `ReadableStream` 的一部分，主要用於創建自定義的可讀流。這個控制器提供了一系列方法和屬性，幫助開發者控制流的數據輸出，以及處理流中的數據。使用 `ReadableStreamDefaultController` 可以在流中推送數據、終止流的輸出或監控流的狀態。

### 主要功能
- **管理數據流輸出**：使用 `enqueue()` 方法可以將數據推入流中。
- **終止數據流**：使用 `close()` 方法可以關閉流，不再輸出數據。
- **處理錯誤**：使用 `error()` 方法可以在發生錯誤時終止流並報告錯誤。

### 使用方式
要使用 `ReadableStreamDefaultController`，首先需要創建一個 `ReadableStream`，並在其構造器中提供一個拉取函數（pull function），該函數的第一個參數就是 `ReadableStreamDefaultController` 的實例：

```javascript
const stream = new ReadableStream({
  start(controller) {
    // 初始化時可執行的代碼
  },
  pull(controller) {
    // 每次需要更多數據時調用
    controller.enqueue('一些數據');
  },
  cancel() {
    // 處理流取消的情況
  }
});
```

## 示例
以下是 `ReadableStreamDefaultController` 的基本使用示例：

### 基本示例
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
  console.log(value); // 輸出: Hello
});
```

### 處理錯誤
```javascript
const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello');
    controller.error('出現錯誤');
  }
});

const reader = readableStream.getReader();
reader.read().catch(error => {
  console.error(error); // 輸出: 出現錯誤
});
```

## 解釋
在使用 `ReadableStreamDefaultController` 時，開發者需要注意以下幾點：

- **流的狀態**：使用 `enqueue()`、`close()` 和 `error()` 方法時，需要注意當前流的狀態，避免對已關閉或出現錯誤的流進行操作。
- **異步操作**：拉取函數（pull function）可以是異步的，確保在適當的時間點推送數據。
- **性能考量**：不應過於頻繁地推送數據，這可能會影響性能，特別是在處理大量數據時。

## 一句總結
`ReadableStreamDefaultController` 是一個用於控制 JavaScript 可讀流的重要接口，提供多種方法來管理數據的生成和流的狀態。