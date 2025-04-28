<!--
Meta Description: # MIDIOutput: 在 JavaScript 中的 MIDI 输出控制 ## 概述 MIDIOutput 是 Web MIDI API 的一部分，允许开发者通过 JavaScript 直接与 MIDI 输出设备进行交互。此功能使得网页应用能够发送 MIDI 消息，从而控制乐器和音频软件。 #...
Meta Keywords: midi, midioutput, send, javascript, data
-->

# MIDIOutput: 在 JavaScript 中的 MIDI 输出控制

## 概述
MIDIOutput 是 Web MIDI API 的一部分，允许开发者通过 JavaScript 直接与 MIDI 输出设备进行交互。此功能使得网页应用能够发送 MIDI 消息，从而控制乐器和音频软件。

## 文档
### 目的
MIDIOutput 使得开发者可以向 MIDI 设备发送数据。通过它，可以实现实时音乐创作、音频控制和与 MIDI 设备的互动。

### 使用方法
要使用 MIDIOutput，首先需要请求 MIDI 权限并获取可用的 MIDI 设备。以下是主要步骤：

1. **请求 MIDI 权限**：
   使用 `navigator.requestMIDIAccess()` 方法请求 MIDI 设备的访问权限。

2. **获取 MIDIOutput**：
   在成功回调中，可以访问所有连接的 MIDI 输出设备。

3. **发送 MIDI 消息**：
   使用 `send()` 方法向 MIDI 设备发送消息。

### 详细说明
- **MIDIOutput 对象**：代表一个 MIDI 输出端口，包含用于发送信息的方法。
- **send(data)**：此方法用于发送消息给 MIDI 设备。`data` 参数是一个表示 MIDI 消息的数组，例如：[144, 60, 127] 表示开启音符60，力度为127。
- **send(data, timestamp)**：可选的 `timestamp` 参数允许指定消息发送的时间。

## 示例
以下是基本的使用示例：

```javascript
// 请求 MIDI 访问
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    // 获取所有输出端口
    const outputs = midiAccess.outputs;
    for (let output of outputs.values()) {
        // 发送 MIDI 消息
        output.send([144, 60, 127]); // 开启音符60
        output.send([128, 60, 0]);   // 关闭音符60
    }
}

function onMIDIFailure() {
    console.error("无法访问 MIDI 设备");
}
```

## 说明
- **兼容性**：确保您的浏览器支持 Web MIDI API。并不是所有浏览器都默认启用此功能。
- **权限问题**：在某些情况下，用户需要手动授予 MIDI 访问权限。
- **设备连接状态**：在发送消息之前，确保 MIDI 设备已经连接并可用。

## 一句话总结
MIDIOutput 是 JavaScript 中用于与 MIDI 输出设备进行交互的强大工具，允许开发者发送实时音乐数据。