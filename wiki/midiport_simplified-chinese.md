<!--
Meta Description: # MIDIPort：JavaScript 中的 MIDI 端口接口 ## 概述 MIDIPort 是 Web MIDI API 中的一个接口，允许网页应用程序与 MIDI 设备进行交互。通过 MIDIPort，开发者可以读取 MIDI 数据、发送 MIDI 消息以及管理 MIDI 连接，为音乐创作...
Meta Keywords: midi, midiport, input, output, midiaccess
-->

# MIDIPort：JavaScript 中的 MIDI 端口接口

## 概述
MIDIPort 是 Web MIDI API 中的一个接口，允许网页应用程序与 MIDI 设备进行交互。通过 MIDIPort，开发者可以读取 MIDI 数据、发送 MIDI 消息以及管理 MIDI 连接，为音乐创作和实时表演提供了强大的功能。

## 文档
### 目的
MIDIPort 接口的主要目的是提供与 MIDI 设备的通信能力。它使开发者能够访问连接到计算机的 MIDI 设备，处理 MIDI 消息和事件。

### 用法
MIDIPort 接口通常通过 `navigator.requestMIDIAccess()` 方法访问。该方法返回一个 `MIDIAccess` 对象，开发者可以通过该对象获取所有可用的 MIDI 端口。

### 详细信息
- **属性**：
  - `id`: 端口的唯一标识符。
  - `name`: 端口的名称。
  - `state`: 端口的状态（如 "connected" 或 "disconnected"）。
  - `type`: 端口的类型（如 "input" 或 "output"）。

- **方法**：
  - `send(data)`: 发送 MIDI 消息到输出端口。

- **事件**：
  - `onstatechange`: 监控端口状态变化的事件。

## 示例
### 基本用法示例
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    const outputs = midiAccess.outputs;

    inputs.forEach((input) => {
        console.log(`Input Port: ${input.name}`);
        input.onmidimessage = (message) => {
            console.log(`Received message: ${message.data}`);
        };
    });

    outputs.forEach((output) => {
        console.log(`Output Port: ${output.name}`);
        output.send([0x90, 60, 0x7f]); // 发送 MIDI 消息
    });
}).catch(function(error) {
    console.error("MIDI Access failed: ", error);
});
```

## 解释
### 常见问题和注意事项
1. **浏览器兼容性**：并非所有浏览器都支持 Web MIDI API。请确保在支持的浏览器中测试您的代码。
2. **安全性**：由于 Web MIDI API 涉及设备访问，确保您的网站使用 HTTPS 协议。
3. **状态变化**：为了监控 MIDI 端口的状态变化，您需要为 `onstatechange` 事件添加事件监听器。
4. **MIDI 消息格式**：了解 MIDI 消息的格式和结构是发送和接收消息的关键。

## 一句话总结
MIDIPort 是 JavaScript 中用于与 MIDI 设备进行通信的接口，简化了音乐应用程序的开发。