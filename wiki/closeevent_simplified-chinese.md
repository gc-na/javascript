<!--
Meta Description: # CloseEvent: JavaScript 中的关闭事件 ## 概述 `CloseEvent` 是 JavaScript 中用于表示 WebSocket 连接关闭的事件对象。它提供了有关连接关闭原因的信息，使开发者能够处理连接终止后的逻辑。 ## 文档 `CloseEvent` 是事件对象的一...
Meta Keywords: closeevent, websocket, socket, event, console
-->

# CloseEvent: JavaScript 中的关闭事件

## 概述
`CloseEvent` 是 JavaScript 中用于表示 WebSocket 连接关闭的事件对象。它提供了有关连接关闭原因的信息，使开发者能够处理连接终止后的逻辑。

## 文档
`CloseEvent` 是事件对象的一种，主要在 WebSocket API 中使用。当 WebSocket 连接关闭时，会触发该事件。`CloseEvent` 对象包含几个重要属性，帮助开发者理解连接关闭的原因及状态。

### 属性
- `code`：一个数字，表示关闭的状态码。常用的状态码包括 1000（正常关闭）和 1006（异常关闭）。
- `reason`：一个字符串，描述关闭的原因。通常由服务器提供，开发者可以根据这个信息进行相应处理。
- `wasClean`：一个布尔值，指示连接是否正常关闭。如果为 `true`，表示连接是干净关闭的；如果为 `false`，表示连接是异常关闭的。

### 使用
要使用 `CloseEvent`，需要在 WebSocket 对象上添加一个事件监听器来处理 `close` 事件。例如：

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('close', function(event) {
    console.log('连接关闭，状态码:', event.code);
    console.log('关闭原因:', event.reason);
    console.log('是否正常关闭:', event.wasClean);
});
```

## 示例
以下是一个使用 `CloseEvent` 的基本示例：

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    console.log('连接已打开');
};

socket.onclose = function(event) {
    console.log('连接已关闭');
    console.log('状态码:', event.code);
    console.log('关闭原因:', event.reason);
    console.log('是否正常关闭:', event.wasClean);
};

// 模拟关闭连接
setTimeout(() => {
    socket.close(1000, '完成通信');
}, 3000);
```

## 说明
在使用 `CloseEvent` 时，有几个常见问题需要注意：

- **状态码的选择**：在关闭 WebSocket 连接时，确保使用合适的状态码。错误的状态码可能导致客户端无法正确理解关闭的原因。
- **异常关闭处理**：如果 `wasClean` 属性为 `false`，应考虑实现重连机制或提示用户连接异常。
- **浏览器兼容性**：虽然大多数现代浏览器都支持 `CloseEvent`，但仍应在使用前检查浏览器的兼容性。

## 一句总结
`CloseEvent` 是用于处理 WebSocket 连接关闭事件的对象，提供了状态码、原因和关闭是否正常的信息。