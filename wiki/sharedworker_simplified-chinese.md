<!--
Meta Description: # JavaScript SharedWorker 详解与应用 ## 概述 SharedWorker 是一种 Web Worker 类型，用于在多个浏览器窗口或标签页之间共享相同的工作线程，提供了一种高效的方式来处理多个脚本之间的共享数据和通信。 ## 文档 ### 目的 SharedWorker ...
Meta Keywords: worker, sharedworker, port, event, javascript
-->

# JavaScript SharedWorker 详解与应用

## 概述
SharedWorker 是一种 Web Worker 类型，用于在多个浏览器窗口或标签页之间共享相同的工作线程，提供了一种高效的方式来处理多个脚本之间的共享数据和通信。

## 文档
### 目的
SharedWorker 旨在让多个浏览器上下文（如窗口、标签页或 iframe）能够共享同一个 Worker 实例，从而减少资源消耗并提高性能。

### 用法
要使用 SharedWorker，需要通过 `SharedWorker` 构造函数创建一个 Worker 实例，并使用 `postMessage` 方法与主线程或其他 Worker 进行通信。

### 详细信息
- **构造函数**： `new SharedWorker(scriptURL, options)`
  - `scriptURL`：Worker 脚本的 URL。
  - `options`（可选）：一个对象，可以包含 `name` 属性，用于命名 Worker。
  
- **事件**：
  - `connect`：当新的连接请求到达时触发。
  
- **通信**：
  - 使用 `port` 属性访问 SharedWorker 的 MessagePort 对象，该对象可以用来发送和接收消息。

## 示例
以下是一个简单的 SharedWorker 示例：

**worker.js**
```javascript
self.onconnect = function(event) {
  const port = event.ports[0];
  port.onmessage = function(event) {
    port.postMessage('收到消息: ' + event.data);
  };
};
```

**主线程**
```javascript
const worker = new SharedWorker('worker.js');

worker.port.start(); // 启动端口

worker.port.onmessage = function(event) {
  console.log(event.data); // 处理来自 Worker 的消息
};

worker.port.postMessage('Hello, Worker!'); // 发送消息到 Worker
```

## 说明
- **跨域问题**：确保 Worker 的脚本与主线程在同一源上，否则将面临跨域访问的限制。
- **浏览器支持**：并非所有浏览器都支持 SharedWorker，特别是一些较老的版本，建议在使用前检查兼容性。
- **连接数限制**：每个 SharedWorker 有最大连接数限制，通常为 50 个连接。

## 一句话总结
SharedWorker 提供了一种在多个浏览器上下文中共享高效 Worker 的机制。