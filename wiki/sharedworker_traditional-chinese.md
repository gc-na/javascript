<!--
Meta Description: # SharedWorker 在 JavaScript 中的應用與實踐 ## 摘要 SharedWorker 是一種 JavaScript Web Worker，允許多個瀏覽器上下文（如不同的標籤頁或 iframe）共享同一個 Worker 實例，從而實現跨標籤頁的數據共享和通信。 ## 文件說明 ...
Meta Keywords: worker, sharedworker, port, event, javascript
-->

# SharedWorker 在 JavaScript 中的應用與實踐

## 摘要
SharedWorker 是一種 JavaScript Web Worker，允許多個瀏覽器上下文（如不同的標籤頁或 iframe）共享同一個 Worker 實例，從而實現跨標籤頁的數據共享和通信。

## 文件說明
SharedWorker 主要用於需要在多個瀏覽器上下文之間共享資料的情況。這使得應用程序可以實現更高效的資源使用和更流暢的用戶體驗。SharedWorker 透過 `SharedWorker` 建構子來創建，並使用 `port` 與其他上下文進行通信。

### 目的
- 共享資料：在多個標籤頁或 iframe 之間傳遞數據。
- 減少資源使用：避免重複加載相同的資源。
- 提高性能：可以在背景中執行任務而不影響主線程。

### 用法
要使用 SharedWorker，您需要按照以下步驟進行：

1. **創建 Shared Worker**：
   ```javascript
   const worker = new SharedWorker('worker.js');
   ```

2. **與 Worker 通信**：
   使用 `port` 屬性來發送和接收消息。
   ```javascript
   worker.port.postMessage('Hello, worker!');
   ```

3. **監聽消息**：
   在 Worker 中，使用 `onmessage` 事件來接收來自主線程的消息。
   ```javascript
   self.onconnect = function(event) {
       const port = event.ports[0];
       port.onmessage = function(event) {
           console.log('Received message:', event.data);
           port.postMessage('Hello, main thread!');
       };
   };
   ```

## 範例
以下是一個簡單的範例，展示如何使用 SharedWorker 進行基本的消息傳遞：

**worker.js**
```javascript
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        console.log('Message from main:', event.data);
        port.postMessage('Message received!');
    };
};
```

**main.js**
```javascript
const worker = new SharedWorker('worker.js');
worker.port.start();

worker.port.onmessage = function(event) {
    console.log('Message from worker:', event.data);
};

worker.port.postMessage('Hello from main!');
```

## 解釋
在使用 SharedWorker 時，有一些常見的陷阱和注意事項：

- **瀏覽器支持**：並非所有瀏覽器都支持 SharedWorker。檢查瀏覽器兼容性是必要的。
- **安全性**：SharedWorker 僅在同一源的上下文之間共享數據，因此請確保您的應用遵循同源策略。
- **連接數量**：每個 SharedWorker 可以處理多個連接，但過多的連接可能會導致性能問題。
- **生命週期**：SharedWorker 的生命週期取決於其所有端口的連接狀態。如果所有端口都關閉，Worker 會終止。

## 一句總結
SharedWorker 是一種強大的工具，可以在多個瀏覽器上下文之間共享數據，從而提高應用程序的性能和用戶體驗。