<!--
Meta Description: # AudioBufferSourceNode：JavaScript中的音频缓冲源节点 ## 概述 `AudioBufferSourceNode` 是 Web Audio API 中的一个接口，用于播放存储在 `AudioBuffer` 中的音频数据。它是实现音频播放的核心组成部分，能够提供多种控制...
Meta Keywords: audiocontext, audiobuffersourcenode, sourcenode, then, buffer
-->

# AudioBufferSourceNode：JavaScript中的音频缓冲源节点

## 概述
`AudioBufferSourceNode` 是 Web Audio API 中的一个接口，用于播放存储在 `AudioBuffer` 中的音频数据。它是实现音频播放的核心组成部分，能够提供多种控制音频播放的功能，如循环、音量调节和播放速度调整。

## 文档
`AudioBufferSourceNode` 主要用于从内存中播放音频数据，通常与 `AudioContext` 结合使用。通过创建 `AudioBufferSourceNode`，开发者可以使用音频缓冲区中的数据进行播放。以下是该节点的主要特性和用法：

### 创建音频缓冲源节点
要创建一个 `AudioBufferSourceNode`，需要一个 `AudioContext` 实例，然后调用其 `createBufferSource()` 方法。示例代码如下：

```javascript
const audioContext = new AudioContext();
const sourceNode = audioContext.createBufferSource();
```

### 音频缓冲区的加载
在使用 `AudioBufferSourceNode` 播放音频之前，必须先加载音频数据到 `AudioBuffer`。通常可以使用 `fetch` 和 `decodeAudioData` 方法来完成音频数据的加载与解码。

```javascript
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    sourceNode.buffer = buffer;
  });
```

### 播放音频
使用 `start()` 方法可以开始播放音频，`stop()` 方法则可以停止播放。

```javascript
sourceNode.start();
sourceNode.stop();
```

## 示例
以下是一个完整的示例，展示了如何使用 `AudioBufferSourceNode` 播放音频：

```javascript
const audioContext = new AudioContext();

fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const sourceNode = audioContext.createBufferSource();
    sourceNode.buffer = buffer;
    
    // 连接到音频上下文的目标
    sourceNode.connect(audioContext.destination);
    
    // 播放音频
    sourceNode.start();
  })
  .catch(error => console.error('Error with decoding audio data', error));
```

## 说明
在使用 `AudioBufferSourceNode` 时，有几个常见的注意事项：

- **一次性使用**：每个 `AudioBufferSourceNode` 只能播放一次，播放后无法重复使用。如果需要再次播放，必须创建一个新的实例。
  
- **音频上下文状态**：确保 `AudioContext` 在播放音频时处于“运行”状态。若处于“暂停”或“停止”状态，音频将无法播放。

- **跨域问题**：如果音频文件存储在不同的服务器上，可能会遇到跨域问题。确保服务器正确设置 CORS 头以允许音频加载。

## 一句话总结
`AudioBufferSourceNode` 是用于播放 `AudioBuffer` 中音频数据的 Web Audio API 组件，提供灵活的音频控制功能。