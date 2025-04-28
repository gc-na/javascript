<!--
Meta Description: # MIDIInput: JavaScript中的MIDI输入接口 ## 摘要 MIDIInput 是 Web MIDI API 中的一个接口，允许开发者在网页应用中接收来自 MIDI 设备的输入信号，用于音乐制作、实时表演和其他音频相关的应用。 ## 文档 ### 目的 MIDIInput 接口提...
Meta Keywords: midi, midiinput, web, api, midiaccess
-->

# MIDIInput: JavaScript中的MIDI输入接口

## 摘要
MIDIInput 是 Web MIDI API 中的一个接口，允许开发者在网页应用中接收来自 MIDI 设备的输入信号，用于音乐制作、实时表演和其他音频相关的应用。

## 文档
### 目的
MIDIInput 接口提供了一种方法来与连接到计算机的 MIDI 设备进行交互，使开发者能够接收 MIDI 消息并对其进行处理。这在音乐应用、游戏和互动表演中非常有用。

### 用法
要使用 MIDIInput，开发者首先需要请求 MIDI 设备的访问权限，然后通过 `navigator.requestMIDIAccess()` 方法获取 MIDIAccess 对象。每个 MIDIInput 对象都有一个 `onmidimessage` 事件，用于处理接收到的 MIDI 消息。

#### 示例代码
```javascript
// 请求 MIDI 访问
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    // 获取输入设备列表
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        // 为每个输入设备添加事件监听器
        input.onmidimessage = handleMIDIMessage;
    });
}

function onMIDIFailure() {
    console.error('无法访问 MIDI 设备');
}

function handleMIDIMessage(event) {
    const [status, note, velocity] = event.data;
    console.log(`收到 MIDI 消息: 状态 ${status}, 音符 ${note}, 力度 ${velocity}`);
}
```

## 解释
在使用 MIDIInput 时，有一些常见的问题和注意事项：

1. **权限问题**: 在某些浏览器中，访问 MIDI 设备需要用户的明确授权。确保用户已允许访问 MIDI 设备。
2. **设备连接**: 确保你的 MIDI 设备已正确连接，并且浏览器支持 Web MIDI API。
3. **事件处理**: 每个 MIDIInput 设备只能有一个 `onmidimessage` 事件处理器。如果需要处理多个事件，考虑在事件处理器中添加逻辑。
4. **浏览器支持**: 并非所有浏览器都支持 Web MIDI API。建议在使用之前查阅浏览器兼容性列表。

## 一句话总结
MIDIInput 接口使开发者能够在 JavaScript 应用中有效接收和处理来自 MIDI 设备的输入信号。