<!--
Meta Description: # AudioWorkletNode：JavaScript中的音频处理新利器 ## 概述 AudioWorkletNode 是 Web Audio API 的一部分，允许开发者创建自定义音频处理节点，以实现高效且低延迟的音频处理。它提供了一种灵活的方式来处理音频流，适用于实时音频应用程序。 ## 文...
Meta Keywords: audioworkletnode, audiocontext, audioworkletprocessor, const, channel
-->

# AudioWorkletNode：JavaScript中的音频处理新利器

## 概述
AudioWorkletNode 是 Web Audio API 的一部分，允许开发者创建自定义音频处理节点，以实现高效且低延迟的音频处理。它提供了一种灵活的方式来处理音频流，适用于实时音频应用程序。

## 文档
### 目的
AudioWorkletNode 旨在为音频开发者提供更大的灵活性和控制能力，使他们可以在浏览器中运行自定义音频处理算法。

### 用法
要使用 AudioWorkletNode，首先需要创建一个 AudioWorkletProcessor 类，并在其中定义音频处理逻辑。接着，使用 AudioContext 的 `audioWorklet.addModule()` 方法加载该处理器，然后创建 AudioWorkletNode 实例。

### 详细信息
- **构造函数**: `AudioWorkletNode` 通过 `AudioContext.createAudioWorkletNode()` 方法创建。
- **参数**:
  - `name`: 处理器的名称，必须与在 audio worklet 模块中定义的处理器名称一致。
  - `options`: 可选参数，允许设置输入输出通道数量及其他选项。
- **属性**:
  - `port`: 用于与 AudioWorkletProcessor 进行通信的 MessagePort。
- **方法**:
  - `connect()`: 将节点连接到其他音频节点。
  - `disconnect()`: 断开节点连接。

## 示例
### 基本用法示例
```javascript
// 创建音频上下文
const audioContext = new AudioContext();

// 定义 AudioWorkletProcessor
class MyProcessor extends AudioWorkletProcessor {
    process(inputs, outputs, parameters) {
        const output = outputs[0];
        for (let channel = 0; channel < output.length; ++channel) {
            const outputChannel = output[channel];
            for (let i = 0; i < outputChannel.length; ++i) {
                outputChannel[i] = Math.random(); // 示例：产生随机音频
            }
        }
        return true; // 持续处理
    }
}

// 注册处理器模块
audioContext.audioWorklet.addModule('my-processor.js').then(() => {
    const myNode = new AudioWorkletNode(audioContext, 'my-processor');
    myNode.connect(audioContext.destination);
});
```

## 说明
- **常见问题**:
  - 确保在使用 AudioWorkletNode 之前已正确加载处理器模块。
  - 注意音频处理的性能，尽量避免过于复杂的计算，以确保低延迟。
- **注意事项**:
  - AudioWorkletNode 是异步加载的，确保在模块加载完成后再创建节点。
  - 跨域问题可能影响模块加载，确保设置了正确的 CORS 策略。

## 一句话总结
AudioWorkletNode 允许开发者在浏览器中创建高效的自定义音频处理节点，以实现实时音频应用。