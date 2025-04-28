<!--
Meta Description: # PresentationConnectionAvailableEvent: JavaScript 中的演示连接可用事件 ## 概述 `PresentationConnectionAvailableEvent` 是一种 JavaScript 事件，用于在 Presentation API 中指示有...
Meta Keywords: presentationreceiver, presentationconnectionavailableevent, event, javascript, presentation
-->

# PresentationConnectionAvailableEvent: JavaScript 中的演示连接可用事件

## 概述
`PresentationConnectionAvailableEvent` 是一种 JavaScript 事件，用于在 Presentation API 中指示有新的演示连接可用。当设备之间建立演示连接时，开发者可以通过该事件获取连接信息并进行相应处理。

## 文档
### 目的
`PresentationConnectionAvailableEvent` 事件主要用于处理新的演示连接。在 Web 应用中，开发者可以通过监听此事件来发现和管理演示连接，从而增强用户体验。

### 用法
在使用 `PresentationConnectionAvailableEvent` 之前，开发者需要确保 Presentation API 被支持。通常，这涉及到以下步骤：

1. 创建一个 `PresentationReceiver` 实例。
2. 监听 `connectionavailable` 事件。
3. 在事件处理器中，获取并处理新的连接。

```javascript
const presentationReceiver = new PresentationReceiver();

presentationReceiver.addEventListener('connectionavailable', (event) => {
    console.log('新的演示连接可用:', event.connection);
});

// 开始接收演示连接
presentationReceiver.start();
```

### 详细信息
- **事件类型**: `PresentationConnectionAvailableEvent`
- **属性**:
  - `connection`: 返回新连接的 `PresentationConnection` 对象，允许开发者与连接的演示设备进行交互。
  
### 示例
以下是一个基本的示例，展示了如何使用 `PresentationConnectionAvailableEvent`：

```javascript
const presentationReceiver = new PresentationReceiver();

presentationReceiver.addEventListener('connectionavailable', (event) => {
    console.log('新的演示连接:', event.connection);
    
    event.connection.addEventListener('message', (messageEvent) => {
        console.log('收到消息:', messageEvent.data);
    });
});

// 开始接收演示连接
presentationReceiver.start();
```

## 解释
- **常见问题**:
  - **事件未触发**: 确保设备支持 Presentation API 并且网络连接正常。
  - **未能处理连接**: 确保在正确的上下文中处理连接，例如在事件监听器内部。

- **注意事项**:
  - 仅在支持 Presentation API 的浏览器中使用。
  - 处理连接时，确保已正确处理各种事件（如 `message` 和 `close`）。

## 一句话总结
`PresentationConnectionAvailableEvent` 事件用于检测和处理新的演示连接，提升 Web 应用的交互性和用户体验。