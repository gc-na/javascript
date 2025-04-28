<!--
Meta Description: # JavaScript 的 SharedWorker：多執行緒共享工作者概述 ## 簡介 SharedWorker 是一個 JavaScript Web API，允許多個瀏覽器窗口或標籤頁共享同一個工作者執行緒，使得它們能夠在彼此之間傳遞訊息。這對於需要在不同上下文中共享狀態的應用程式非常有用。 ...
Meta Keywords: sharedworker, javascript, worker, port, event
-->

# JavaScript 的 SharedWorker：多執行緒共享工作者概述

## 簡介
SharedWorker 是一個 JavaScript Web API，允許多個瀏覽器窗口或標籤頁共享同一個工作者執行緒，使得它們能夠在彼此之間傳遞訊息。這對於需要在不同上下文中共享狀態的應用程式非常有用。

## 文檔
SharedWorker 的主要目的是提升性能和資源的使用效率。與傳統的 Web Worker 不同，SharedWorker 可以被多個瀏覽器上下文（例如，不同的標籤頁或窗口）同時使用。這意味著你可以在一個地方創建數據或任務的共享實例，然後在其他地方輕鬆訪問。

### 用法
要使用 SharedWorker，首先需要創建一個 SharedWorker 實例，然後在其文件中定義所需的事件處理程序。以下是基本的使用步驟：

1. 創建一個 JavaScript 文件作為工作者，例如 `sharedWorker.js`。
2. 在該文件中，使用 `onconnect` 事件來處理連接到工作者的上下文。
3. 在主 JavaScript 文件中，創建 SharedWorker 實例並連接到該工作者文件。

### 代碼示例
以下是如何創建和使用 SharedWorker 的基本示例：

**sharedWorker.js**
```javascript
let connections = [];

onconnect = function(event) {
    const port = event.ports[0];
    connections.push(port);

    port.onmessage = function(e) {
        for (let connection of connections) {
            connection.postMessage(e.data);
        }
    };
};
```

**main.js**
```javascript
const worker = new SharedWorker('sharedWorker.js');

worker.port.onmessage = function(event) {
    console.log('Received from worker:', event.data);
};

worker.port.start();
worker.port.postMessage('Hello from main script!');
```

## 解釋
使用 SharedWorker 時，有幾個常見的陷阱和注意事項：

- **跨域限制**：SharedWorker 只能在同一來源（origin）下使用。不同域名之間的上下文無法共享同一個工作者。
- **生命週期**：SharedWorker 的生命週期與它的所有連接有關。當最後一個連接關閉時，SharedWorker 將停止運行。
- **性能考量**：雖然 SharedWorker 可以提高性能，但過多的連接可能導致資源競爭，需謹慎使用。

## 一句總結
SharedWorker 是一個強大的 JavaScript 特性，允許多個瀏覽器上下文共享一個工作者執行緒，從而提升應用程式的性能與效率。