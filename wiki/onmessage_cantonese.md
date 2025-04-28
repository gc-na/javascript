<!--
Meta Description: # JavaScript 中的 onmessage 事件處理器 ## 簡介 `onmessage` 是一個 JavaScript 事件處理器，用於處理 Web Worker 和其他消息通訊的事件。它允許主線程與 worker 之間進行異步通信，使得網頁應用程序可以在不阻塞主執行緒的情況下處理複雜的計...
Meta Keywords: worker, onmessage, event, javascript, data
-->

# JavaScript 中的 onmessage 事件處理器

## 簡介
`onmessage` 是一個 JavaScript 事件處理器，用於處理 Web Worker 和其他消息通訊的事件。它允許主線程與 worker 之間進行異步通信，使得網頁應用程序可以在不阻塞主執行緒的情況下處理複雜的計算。

## 文件說明
`onmessage` 事件在 Web Worker 或其他上下文中接收消息時觸發。這些消息可以是來自主線程或其他 Worker 的數據。使用 `onmessage` 可以接收、處理和響應這些消息，從而實現高效的並行處理。

### 目的
- 允許主線程與 Worker 之間的通信。
- 支持異步處理，提升應用性能。

### 使用方法
要使用 `onmessage`，需要為 Worker 實例設置相應的事件處理器。當 Worker 收到消息後，會自動觸發該事件。

```javascript
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log('Received message from worker:', event.data);
};

// 發送消息到 Worker
worker.postMessage('Hello, Worker!');
```

## 示例
### 基本使用
以下是一個簡單的例子，展示如何使用 `onmessage` 來接收 Worker 發送的消息。

**主線程 (main.js):**
```javascript
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log('Received:', event.data);
};

worker.postMessage('Start working!');
```

**Worker (worker.js):**
```javascript
onmessage = function(event) {
    console.log('Message from main thread:', event.data);
    postMessage('Work done!');
};
```

在這個例子中，主線程發送消息給 Worker，Worker 接收後進行處理，然後回傳結果。

## 解釋
### 常見問題
1. **事件未觸發**：如果 `onmessage` 沒有被觸發，請檢查是否正確設置了 Worker，並確保 Worker 正在運行。
2. **數據傳遞**：確保發送的數據是可序列化的。某些對象（如 DOM 元素）無法被傳遞。
3. **多個消息**：如果需要處理多個不同的消息類型，可以在 `onmessage` 內部根據 `event.data` 的內容進行判斷。

### 附加說明
- `onmessage` 事件處理器接收一個事件對象，該對象包含一個 `data` 屬性，用於訪問接收到的消息。
- 可以使用 `addEventListener` 方法來設置事件處理器，以便於添加多個處理器。

## 一句總結
`onmessage` 是一個關鍵的事件處理器，用於在 JavaScript 中實現主線程和 Worker 之間的異步消息通信。