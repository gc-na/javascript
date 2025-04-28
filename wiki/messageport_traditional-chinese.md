<!--
Meta Description: # MessagePort - JavaScript 中的訊息通道 ## 概要 `MessagePort` 是一種在 Web Worker 和主執行緒之間進行通訊的接口。它允許在不同的執行上下文之間傳遞訊息，從而實現高效的非同步處理。 ## 文檔 ### 目的 `MessagePort` 用於在多個...
Meta Keywords: messageport, worker, channel, event, javascript
-->

# MessagePort - JavaScript 中的訊息通道

## 概要
`MessagePort` 是一種在 Web Worker 和主執行緒之間進行通訊的接口。它允許在不同的執行上下文之間傳遞訊息，從而實現高效的非同步處理。

## 文檔
### 目的
`MessagePort` 用於在多個執行環境之間傳遞訊息，特別是 Web Workers 和主執行緒。它使得不同上下文中的程式碼可以安全地交換資料，而不會互相干擾。

### 使用方式
`MessagePort` 通常與 `MessageChannel` 一起使用。`MessageChannel` 可以創建一對 `MessagePort`，這兩個端口可以用於雙向通訊。當一個端口發送訊息時，另一個端口可以接收到該訊息。

#### 創建 MessageChannel
```javascript
const channel = new MessageChannel();
```

#### 設定事件監聽器
使用 `onmessage` 方法來接收訊息：
```javascript
channel.port1.onmessage = function(event) {
    console.log("Received message:", event.data);
};
```

#### 發送訊息
使用 `postMessage` 方法來發送訊息：
```javascript
channel.port2.postMessage("Hello from port2!");
```

### 詳細說明
- **同時性**：`MessagePort` 是非同步的，這意味著當你發送訊息時，不需要等待接收方處理訊息後才繼續執行其他代碼。
- **安全性**：在不同的執行上下文中使用 `MessagePort` 可以有效隔離資料，避免了直接訪問導致的安全風險。
- **終止**：可以使用 `close()` 方法關閉 `MessagePort`，這將終止與該端口的通訊。

## 範例
### 基本使用範例
以下是使用 `MessagePort` 的基本範例，展示了如何在主執行緒和 Web Worker 之間傳送訊息。

#### 主執行緒
```javascript
const worker = new Worker('worker.js');
const channel = new MessageChannel();

worker.postMessage({ port: channel.port1 }, [channel.port1]);

channel.port2.onmessage = function(event) {
    console.log("Received from worker:", event.data);
};

channel.port2.postMessage("Hello from main thread!");
```

#### Worker (`worker.js`)
```javascript
onmessage = function(event) {
    const port = event.data.port;

    port.onmessage = function(event) {
        console.log("Received from main thread:", event.data);
        port.postMessage("Hello from worker!");
    };
};
```

## 說明
- **常見陷阱**：初學者常常會忘記將 `MessagePort` 的端口傳遞給對方，這會導致無法接收到訊息。
- **序列化**：發送的訊息必須是可序列化的，這意味著不能直接傳遞函數或未序列化的物件。
- **終止後的行為**：一旦端口被關閉（使用 `close()`），將無法再發送或接收訊息，任何這樣的操作都會被忽略。

## 一句總結
`MessagePort` 是一種用於在不同執行上下文間非同步傳遞訊息的強大工具。