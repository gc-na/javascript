<!--
Meta Description: # JavaScript 中的 onmessage 事件處理 ## 摘要 `onmessage` 是一個事件處理器，用於監聽 Web Worker 和主執行緒（主線程）之間的消息通訊。這個功能使得在多執行緒環境中實現異步操作成為可能，從而提高了網頁的性能和響應速度。 ## 文件說明 `onmessa...
Meta Keywords: worker, onmessage, event, javascript, postmessage
-->

# JavaScript 中的 onmessage 事件處理

## 摘要
`onmessage` 是一個事件處理器，用於監聽 Web Worker 和主執行緒（主線程）之間的消息通訊。這個功能使得在多執行緒環境中實現異步操作成為可能，從而提高了網頁的性能和響應速度。

## 文件說明
`onmessage` 是一個事件屬性，通常與 Web Worker 和 `postMessage` 方法一起使用。當從另一個上下文（例如主執行緒或其他 Worker）發送消息時，`onmessage` 事件會被觸發。這使得開發者能夠輕鬆地接收和處理來自不同執行緒的數據。

### 用法
要使用 `onmessage`，您需要為 Worker 或主執行緒設置一個相應的事件處理器。以下是基本的語法結構：

```javascript
worker.onmessage = function(event) {
    // 處理接收到的消息
    console.log(event.data);
};
```

在主執行緒中，您可以使用 `postMessage` 方法將消息發送到 Worker：

```javascript
worker.postMessage("Hello, Worker!");
```

## 範例
以下是 `onmessage` 的基本用法示例：

### 範例 1：基本的 Worker 通信

```javascript
// main.js
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log("Received from worker:", event.data);
};

worker.postMessage("Hello, Worker!");
```

```javascript
// worker.js
onmessage = function(event) {
    console.log("Received from main:", event.data);
    postMessage("Hello, Main!");
};
```

### 範例 2：計算平方的 Worker

```javascript
// main.js
const worker = new Worker('squareWorker.js');

worker.onmessage = function(event) {
    console.log("Square is:", event.data);
};

worker.postMessage(5);
```

```javascript
// squareWorker.js
onmessage = function(event) {
    const result = event.data * event.data;
    postMessage(result);
};
```

## 解釋
使用 `onmessage` 時，開發者應注意以下幾點：

1. **數據傳遞限制**：傳遞的數據必須是可序列化的。對象和陣列可以直接傳遞，但函數和 DOM 元素則無法。
   
2. **異步性**：`onmessage` 事件是異步的，這意味著消息的接收和處理不會阻塞主執行緒。開發者需要確保在處理消息時不會造成競爭條件。

3. **錯誤處理**：在 Worker 中，錯誤處理需要通過 `onerror` 事件來捕獲，因為 `onmessage` 不會捕獲錯誤。

4. **終止 Worker**：當不再需要 Worker 時，應該使用 `worker.terminate()` 方法來終止 Worker，以釋放資源。

## 一句總結
`onmessage` 是 JavaScript 中用於處理 Web Worker 和主執行緒之間消息通訊的重要事件處理器。