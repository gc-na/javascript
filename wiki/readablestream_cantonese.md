<!--
Meta Description: # JavaScript 的 ReadableStream：流式處理數據的強大工具 ## 概述 ReadableStream 是一個 Web API，用於表示可讀的數據流。它允許開發者以非同步的方式讀取數據，特別適合用於處理大文件或網絡請求的數據。 ## 文檔 ### 目的 ReadableStre...
Meta Keywords: readablestream, controller, javascript, value, const
-->

# JavaScript 的 ReadableStream：流式處理數據的強大工具

## 概述
ReadableStream 是一個 Web API，用於表示可讀的數據流。它允許開發者以非同步的方式讀取數據，特別適合用於處理大文件或網絡請求的數據。

## 文檔
### 目的
ReadableStream 提供了一種方法來逐步讀取數據，而不是一次性加載所有數據。這樣可以減少內存使用，提高應用性能，特別是在處理大量數據時。

### 用法
要創建一個 ReadableStream，可以使用以下語法：

```javascript
const readableStream = new ReadableStream({
  start(controller) {
    // 初始化代碼
  },
  pull(controller) {
    // 每次需要更多數據時調用
  },
  cancel() {
    // 清理代碼
  }
});
```

### 屬性和方法
- **start(controller)**: 用於初始化流的代碼，通常用來推送初始數據。
- **pull(controller)**: 當消費者需要更多數據時被調用，這裡可以推送更多數據。
- **cancel()**: 用於清理操作，當讀取流被取消時調用。

## 示例
以下是一個簡單的 ReadableStream 使用範例：

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello');
    controller.enqueue('World');
    controller.close();
  }
});

const reader = stream.getReader();

reader.read().then(({ done, value }) => {
  console.log(value); // 輸出: Hello
});

reader.read().then(({ done, value }) => {
  console.log(value); // 輸出: World
});
```

## 解釋
在使用 ReadableStream 時，有幾個常見的坑要注意：
- **流的可讀性**: 確保在推送數據時，流仍然是可讀的。調用 `close()` 會使流不再可讀。
- **異步行為**: 由於 ReadableStream 是非同步的，確保適當處理 Promise 以避免未處理的錯誤。
- **內存管理**: 在處理大量數據時，確保不會因為未及時消耗流而導致內存溢出。

## 一句總結
ReadableStream 是 JavaScript 中一個強大的API，適合用於高效的數據流處理與讀取。