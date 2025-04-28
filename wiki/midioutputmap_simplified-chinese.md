<!--
Meta Description: # MIDIOutputMap 在 JavaScript 中的使用指南 ## 概述 MIDIOutputMap 是 Web MIDI API 中用于管理 MIDI 输出设备的一个重要接口。它允许开发者在网页应用中与 MIDI 设备进行交互，提供实时的音频和控制信息。 ## 文档 ### 目的 MID...
Meta Keywords: midi, midioutputmap, output, outputs, midioutput
-->

# MIDIOutputMap 在 JavaScript 中的使用指南

## 概述
MIDIOutputMap 是 Web MIDI API 中用于管理 MIDI 输出设备的一个重要接口。它允许开发者在网页应用中与 MIDI 设备进行交互，提供实时的音频和控制信息。

## 文档
### 目的
MIDIOutputMap 提供了一个包含所有可用 MIDI 输出设备的映射，开发者可以通过它来选择和操作特定的 MIDI 设备。

### 用法
使用 MIDIOutputMap 的基本步骤如下：

1. **请求 MIDI 访问权限**：通过 `navigator.requestMIDIAccess()` 请求对 MIDI 设备的访问权限。
2. **获取输出设备**：访问 `outputs` 属性，从中获取 MIDIOutputMap。
3. **发送 MIDI 消息**：使用 MIDIOutput 对象的方法发送 MIDI 消息。

### 详细信息
- **结构**：MIDIOutputMap 是一个类似于 Map 的对象，包含 MIDI 输出设备的 ID 和相应的 MIDIOutput 对象。
- **数据类型**：每个设备的 ID 是字符串，MIDIOutput 对象用于发送 MIDI 消息。
- **事件处理**：MIDIOutputMap 不直接处理事件，但可以通过 MIDIOutput 对象的事件方法来监听设备的状态变化。

## 示例
以下是使用 MIDIOutputMap 的基本示例：

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    // 获取所有 MIDI 输出设备
    const outputs = midiAccess.outputs;
    
    // 遍历输出设备
    outputs.forEach(function(output) {
        console.log(`设备名称: ${output.name}, 设备 ID: ${output.id}`);
        
        // 发送 MIDI 消息
        output.send([144, 60, 0]); // 发送一个音符开始消息
    });
});
```

## 解释
### 常见问题
- **设备不可用**：在某些设备上，可能无法获取到 MIDI 输出设备。确保你的设备已正确连接且兼容。
- **权限问题**：确保浏览器已允许访问 MIDI 设备，否则无法获取 MIDIOutputMap。
- **发送消息格式**：发送的 MIDI 消息必须遵循 MIDI 协议，否则设备可能无法正确响应。

### 注意事项
- 使用 `output.send()` 方法时，参数必须是正确格式的数组。
- 在发送消息后，设备可能需要一定的时间来处理请求。

## 一句话总结
MIDIOutputMap 是 Web MIDI API 的关键接口，允许开发者轻松访问和操作 MIDI 输出设备。