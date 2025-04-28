<!--
Meta Description: # ReadableStreamDefaultController：JavaScript 中的可讀流控制器 ## 摘要 `ReadableStreamDefaultController` 是一個用於控制可讀流的 JavaScript 組件，使開發者能夠更靈活地管理流的數據產出和狀態。 ## 文檔 `...
Meta Keywords: controller, readablestreamdefaultcontroller, readablestream, enqueue, javascript
-->

# ReadableStreamDefaultController：JavaScript 中的可讀流控制器

## 摘要
`ReadableStreamDefaultController` 是一個用於控制可讀流的 JavaScript 組件，使開發者能夠更靈活地管理流的數據產出和狀態。

## 文檔
`ReadableStreamDefaultController` 是 `ReadableStream` 的一部分，專門用於管理流的數據推送。它為開發者提供了一組方法，讓開發者可以控制數據如何被讀取和處理。

### 目的
`ReadableStreamDefaultController` 主要用於：
- 控制流的數據產出。
- 管理流的狀態，例如流是否已完成或是否出現錯誤。

### 使用方法
1. **創建可讀流**：在創建 `ReadableStream` 時，可以傳遞一個物件作為配置，該物件中包含一個 `start` 方法，在這個方法中可以獲取 `ReadableStreamDefaultController` 的實例。
2. **控制數據推送**：使用 `controller.enqueue()` 方法可以將數據推送到流中，使用 `controller.close()` 方法可以關閉流，使用 `controller.error()` 方法可以報告錯誤。

### 詳細信息
```javascript
const readableStream = new ReadableStream({
  start(controller) {
    // 使用 controller 來控制數據的推送
    controller.enqueue('Hello');
    controller.enqueue('World');
    controller.close();
  }
});
```
在此範例中，`start` 方法會在流開始時被調用，然後通過 `controller.enqueue()` 方法將數據推送到流中，最後用 `controller.close()` 關閉流。

## 範例
### 基本用法
```javascript
const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('第一個數據');
    controller.enqueue('第二個數據');
    controller.close();
  }
});

const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  console.log(value); // 輸出：第一個數據
});
```
在這個例子中，我們創建了一個可讀流，並在 `start` 方法中推送了兩個數據，然後使用 `getReader()` 方法讀取數據。

## 解釋
當使用 `ReadableStreamDefaultController` 時，有幾個常見的陷阱和注意事項：
- 確保在推送數據時，流的狀態是允許的（例如，在關閉流後再推送數據會導致錯誤）。
- 在 `controller.close()` 或 `controller.error()` 方法被調用後，無法再進行任何數據推送。

## 一句總結
`ReadableStreamDefaultController` 使開發者能夠靈活地控制 JavaScript 中可讀流的數據管理和狀態。