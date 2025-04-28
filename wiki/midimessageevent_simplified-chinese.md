<!--
Meta Description: # MIDIMessageEvent：JavaScript中的MIDI消息事件 ## 概述 `MIDIMessageEvent`是Web MIDI API中的一个接口，用于表示通过MIDI接口接收到的MIDI消息。这允许开发者在网页中与MIDI设备进行交互，从而实现音乐创作、音频应用等功能。 ## ...
Meta Keywords: midimessageevent, inputs, midi, const, onmidisuccess
-->

# MIDIMessageEvent：JavaScript中的MIDI消息事件

## 概述
`MIDIMessageEvent`是Web MIDI API中的一个接口，用于表示通过MIDI接口接收到的MIDI消息。这允许开发者在网页中与MIDI设备进行交互，从而实现音乐创作、音频应用等功能。

## 文档
`MIDIMessageEvent`接口提供了有关MIDI消息的信息。每当MIDI设备发送消息时，`MIDIMessageEvent`对象就会被创建并传递给相关的事件处理程序。该对象包含了MIDI消息的具体数据，允许开发者读取和处理这些信息。

### 属性
- `data`: 一个`Uint8Array`对象，包含了MIDI消息的字节数据。
- `receivedTime`: 一个`DOMHighResTimeStamp`，表示事件接收的精确时间。

### 用法
要使用`MIDIMessageEvent`，首先需要通过Web MIDI API连接到MIDI设备。连接后，可以监听`midimessage`事件，以获取`MIDIMessageEvent`对象。

```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.onmidimessage = handleMIDIMessage;
    });
}

function handleMIDIMessage(event) {
    // event为MIDIMessageEvent对象
    console.log(event.data); // 打印MIDI消息数据
}
```

## 示例
以下是一个基本的使用示例，展示如何接收和处理MIDI消息：

```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.onmidimessage = (event) => {
            const message = event.data;
            const command = message[0];
            const note = message[1];
            console.log(`MIDI Command: ${command}, Note: ${note}`);
        };
    });
}

function onMIDIFailure() {
    console.error('无法访问MIDI设备');
}
```

## 说明
在使用`MIDIMessageEvent`时，有一些常见的陷阱和注意事项：
- 确保浏览器支持Web MIDI API，并在安全上下文中使用（如HTTPS）。
- 处理MIDI消息时，注意字节数组的结构，通常第一个字节是命令，后续字节是参数。
- 不同的MIDI设备可能发送不同类型的消息，开发者需要根据具体需求解析这些消息。

## 一句话总结
`MIDIMessageEvent`是Web MIDI API中用于表示接收到的MIDI消息的接口，使得JavaScript能够与MIDI设备进行有效的交互。