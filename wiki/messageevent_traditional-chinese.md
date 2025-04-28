<!--
Meta Description: # JavaScript 的 MessageEvent 事件 ## 概述 `MessageEvent` 是一個與 Web 應用程序中的消息傳遞相關的事件，通常用於在不同的執行上下文（如 Web Workers、跨源 iframe 或者使用 WebSocket 連接的客戶端和伺服器間）中傳遞數據。 #...
Meta Keywords: worker, javascript, messageevent, message, event
-->

# JavaScript 的 MessageEvent 事件

## 概述
`MessageEvent` 是一個與 Web 應用程序中的消息傳遞相關的事件，通常用於在不同的執行上下文（如 Web Workers、跨源 iframe 或者使用 WebSocket 連接的客戶端和伺服器間）中傳遞數據。

## 文檔
### 目的
`MessageEvent` 讓開發者能夠在不同的執行環境之間安全地傳遞消息，從而促進了應用程序的模組化和性能優化。

### 使用方式
`MessageEvent` 事件通常在使用 `postMessage` 方法時觸發。當一個窗口或 Worker 發送消息後，對應的接收方會接收到 `message` 事件，這個事件的 `data` 屬性包含了發送的內容。

#### 事件屬性
- `data`: 傳遞的消息內容，可以是任何 JavaScript 支持的數據類型。
- `origin`: 發送消息的源，包含協議、主機和端口。
- `lastEventId`: 最近一次事件的 ID（如果有的話）。
- `source`: 發送消息的窗口或 Worker 對象。

### 事件監聽器
要監聽 `MessageEvent`，可以使用以下代碼：
```javascript
window.addEventListener('message', function(event) {
    console.log('Received message:', event.data);
});
```

## 示例
### 基本使用範例
#### 發送消息
```javascript
// 在主窗口中，發送消息到 iframe
const iframe = document.getElementById('myIframe');
iframe.contentWindow.postMessage('Hello from parent!', '*');
```

#### 接收消息
```javascript
// 在 iframe 中，接收主窗口發送的消息
window.addEventListener('message', function(event) {
    console.log('Received message from parent:', event.data);
});
```

### Web Worker 中的使用範例
#### Worker 發送消息
```javascript
// worker.js
self.postMessage('Hello from worker!');
```

#### 主線程接收 Worker 消息
```javascript
const worker = new Worker('worker.js');
worker.addEventListener('message', function(event) {
    console.log('Received message from worker:', event.data);
});
```

## 解釋
使用 `MessageEvent` 時的一些常見陷阱包括：
- 確保正確處理 `origin` 屬性，避免安全風險。僅接受來自可信來源的消息。
- 使用 `event.source` 來確定消息的來源，這樣可以避免意外處理來自不明來源的消息。
- 確保在發送和接收消息時使用正確的數據格式，以避免 JSON 解析錯誤。

## 總結
`MessageEvent` 是一個強大且靈活的工具，用於在不同的執行上下文之間安全地傳遞消息。