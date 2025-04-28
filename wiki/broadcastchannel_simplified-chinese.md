<!--
Meta Description: # JavaScript 中的 BroadcastChannel API：实现跨文档通信 ## 概述 `BroadcastChannel` 是一种 Web API，允许同源的不同窗口、标签页或 iframe 之间进行简单的消息传递。它通过创建一个频道，使得通过该频道发送的消息可以被所有订阅该频道的实...
Meta Keywords: broadcastchannel, channel, javascript, const, event
-->

# JavaScript 中的 BroadcastChannel API：实现跨文档通信

## 概述
`BroadcastChannel` 是一种 Web API，允许同源的不同窗口、标签页或 iframe 之间进行简单的消息传递。它通过创建一个频道，使得通过该频道发送的消息可以被所有订阅该频道的实例接收。

## 文档
### 目的
`BroadcastChannel` 的主要目的是实现浏览器中的多窗口或标签页之间的实时通信。它为应用程序提供了一种轻量级的方式来同步状态或传递信息。

### 使用方法
要使用 `BroadcastChannel`，您需要创建一个新的频道并使用它来发送和接收消息。

#### 创建频道
```javascript
const channel = new BroadcastChannel('channel-name');
```

#### 发送消息
```javascript
channel.postMessage('Hello World');
```

#### 接收消息
```javascript
channel.onmessage = function(event) {
    console.log('Received:', event.data);
};
```

#### 关闭频道
在不再需要通信时，可以关闭频道：
```javascript
channel.close();
```

### 详细信息
- **构造函数**：`BroadcastChannel(channelName)`，其中 `channelName` 是一个字符串，用于标识频道。
- **方法**：
  - `postMessage(message)`：向频道发送消息。
  - `close()`：关闭频道。
- **事件**：
  - `onmessage`：当接收到消息时触发的事件。

## 示例
### 基本用法
以下是一个简单的示例，展示了如何使用 `BroadcastChannel` 实现消息传递：

**发送方**：
```javascript
const channel = new BroadcastChannel('test-channel');

document.getElementById('sendButton').addEventListener('click', () => {
    const message = document.getElementById('messageInput').value;
    channel.postMessage(message);
});
```

**接收方**：
```javascript
const channel = new BroadcastChannel('test-channel');

channel.onmessage = function(event) {
    console.log('Received message:', event.data);
};
```

## 解释
### 常见问题和注意事项
1. **同源限制**：`BroadcastChannel` 仅在同源的文档之间有效。不同源的文档无法通过同一频道进行通信。
2. **消息丢失**：如果接收方在发送方发送消息时未处于活动状态，可能会错过消息。建议使用持久化存储（如 `localStorage`）进行补偿。
3. **性能考虑**：在高频率发送消息的情况下，可能会影响性能，建议合理使用。

## 一句话总结
`BroadcastChannel` 是一个用于在同源的不同浏览器上下文间进行高效消息传递的 Web API。