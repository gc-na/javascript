<!--
Meta Description: # postMessage：JavaScript 中的跨文档消息传递机制 ## 概述 `postMessage` 是一个用于在不同窗口、iframe 或者 Worker 之间安全地传递消息的 JavaScript 方法。它使得跨源通信变得简单而安全，能够有效地处理复杂的 web 应用程序中组件之间的...
Meta Keywords: postmessage, javascript, message, event, targetwindow
-->

# postMessage：JavaScript 中的跨文档消息传递机制

## 概述
`postMessage` 是一个用于在不同窗口、iframe 或者 Worker 之间安全地传递消息的 JavaScript 方法。它使得跨源通信变得简单而安全，能够有效地处理复杂的 web 应用程序中组件之间的交互。

## 文档
### 目的
在现代 web 开发中，常常需要不同源的窗口或标签页之间进行通信。`postMessage` 方法提供了一种安全的方式来实现这一点，避免了常见的跨源问题。

### 使用方法
`postMessage` 方法可以通过以下语法调用：

```javascript
targetWindow.postMessage(message, targetOrigin, [transfer]);
```

- `targetWindow`：要发送消息的目标窗口或 iframe。
- `message`：要发送的消息内容，可以是字符串、对象等。
- `targetOrigin`：指定接收窗口的源，必须与接收方的 origin 匹配，以防止恶意攻击。
- `transfer`（可选）：一个可转移的对象数组。

### 详细说明
- 使用 `postMessage` 时，确保在发送消息时明确指定 `targetOrigin`，以增强安全性。
- 接收方窗口需要添加一个事件监听器来处理接收到的消息，通常使用 `message` 事件来接收。

```javascript
window.addEventListener("message", function(event) {
    // 验证来源
    if (event.origin !== "https://example.com") return; 
   
    // 处理消息
    console.log(event.data);
}, false);
```

## 示例
### 基本用法
以下是一个简单的示例，展示了如何使用 `postMessage` 发送和接收消息：

#### 发送消息
```javascript
const targetWindow = window.open("https://example.com");
targetWindow.postMessage("Hello from parent!", "https://example.com");
```

#### 接收消息
```javascript
window.addEventListener("message", function(event) {
    if (event.origin === "https://example.com") {
        console.log("Received message: " + event.data);
    }
}, false);
```

## 说明
- **常见陷阱**：确保 `targetOrigin` 的设置正确，避免使用 `"*"`，因为这会允许任何来源接收消息，存在安全隐患。
- **性能注意**：`postMessage` 是异步的，发送消息后不会阻塞执行，这意味着你无法立即获取到接收到的消息。
- **JSON 处理**：发送对象时，确保目标窗口能够处理 JSON 格式的数据，使用 `JSON.stringify` 和 `JSON.parse` 进行序列化和反序列化。

## 一句话总结
`postMessage` 是一个安全的 JavaScript 方法，用于在不同来源的窗口之间进行跨文档通信。