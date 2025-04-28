<!--
Meta Description: # JavaScript 中的 BroadcastChannel：有效的跨文檔通訊 ## 概述 BroadcastChannel 是一種 Web API，允許同源的不同瀏覽器上下文（例如不同的標籤頁、窗口或 iframe）之間進行即時的消息傳遞。這使得開發者能夠在應用程序的各個部分之間輕鬆共享數據和...
Meta Keywords: broadcastchannel, channel, javascript, event, api
-->

# JavaScript 中的 BroadcastChannel：有效的跨文檔通訊

## 概述
BroadcastChannel 是一種 Web API，允許同源的不同瀏覽器上下文（例如不同的標籤頁、窗口或 iframe）之間進行即時的消息傳遞。這使得開發者能夠在應用程序的各個部分之間輕鬆共享數據和事件。

## 文檔
### 目的
BroadcastChannel API 旨在簡化在同一源下的多個瀏覽器上下文之間的通訊。開發者可以使用這個 API 發送和接收消息，而不需依賴於其他複雜的通訊方法（如 WebSocket 或 server-sent events）。

### 使用方式
要使用 BroadcastChannel，首先需要創建一個新的 BroadcastChannel 實例，然後使用 `postMessage` 方法發送消息。接收消息的上下文需要為該通道註冊一個事件監聽器。

#### 創建 BroadcastChannel
```javascript
const channel = new BroadcastChannel('channel_name');
```

#### 發送消息
```javascript
channel.postMessage('Hello, World!');
```

#### 接收消息
```javascript
channel.onmessage = (event) => {
    console.log('Received:', event.data);
};
```

### 詳細信息
- **通道名稱**：每個 BroadcastChannel 實例都需要一個唯一的名稱，這個名稱將用於識別該通道。
- **消息格式**：發送的消息可以是任何可序列化的數據，包括字符串、數組和物件。
- **清理**：當不再需要通道時，應使用 `channel.close()` 來關閉通道並釋放資源。

## 示例
### 基本使用範例
以下是一個簡單的範例，展示如何在兩個不同的標籤頁中使用 BroadcastChannel 進行消息傳遞。

#### 標籤頁 1
```javascript
const channel = new BroadcastChannel('my_channel');

channel.onmessage = (event) => {
    console.log('標籤頁 1 收到:', event.data);
};

setInterval(() => {
    channel.postMessage('來自標籤頁 1 的消息');
}, 2000);
```

#### 標籤頁 2
```javascript
const channel = new BroadcastChannel('my_channel');

channel.onmessage = (event) => {
    console.log('標籤頁 2 收到:', event.data);
};

setInterval(() => {
    channel.postMessage('來自標籤頁 2 的消息');
}, 3000);
```

## 解釋
### 常見陷阱與注意事項
- **名稱衝突**：確保通道名稱唯一，否則不同的上下文可能會接收到相同的消息。
- **數據序列化**：傳送的數據必須是可序列化的，否則可能會拋出錯誤。
- **資源管理**：使用完通道後，記得調用 `close()` 方法以釋放資源，否則可能會導致內存泄漏。

## 一句總結
BroadcastChannel 是一個方便的 API，允許在同源的不同瀏覽器上下文中輕鬆地傳遞消息。