<!--
Meta Description: # AudioScheduledSourceNode 在 JavaScript 中的使用 ## 概述 `AudioScheduledSourceNode` 是 Web Audio API 中的一个重要接口，用于表示可调度的音频源节点。它允许开发者在特定时间播放音频，适用于创建复杂的音频应用。 ## ...
Meta Keywords: audiocontext, source, audioscheduledsourcenode, then, buffer
-->

# AudioScheduledSourceNode 在 JavaScript 中的使用

## 概述
`AudioScheduledSourceNode` 是 Web Audio API 中的一个重要接口，用于表示可调度的音频源节点。它允许开发者在特定时间播放音频，适用于创建复杂的音频应用。

## 文档
`AudioScheduledSourceNode` 是一个抽象类，不能直接实例化，但它的子类包括 `AudioBufferSourceNode` 和 `ConstantSourceNode`。该节点的主要目的是提供音频的调度功能，使得开发者能够在准确的时间点控制音频的播放。

### 目的
`AudioScheduledSourceNode` 的设计目的是为了支持音频的精确调度，使得开发者能够在音频图中创建基于时间的音频效果。

### 使用
要使用 `AudioScheduledSourceNode`，开发者通常会实例化其子类。以下是 `AudioBufferSourceNode` 的基本用法示例：

1. 创建音频上下文：
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. 加载音频文件并创建 `AudioBufferSourceNode`：
   ```javascript
   let source;
   fetch('path/to/audio/file.mp3')
       .then(response => response.arrayBuffer())
       .then(data => audioContext.decodeAudioData(data))
       .then(buffer => {
           source = audioContext.createBufferSource();
           source.buffer = buffer;
       });
   ```

3. 调度音频播放：
   ```javascript
   source.start(audioContext.currentTime + 1); // 在当前时间之后1秒开始播放
   ```

## 示例
以下是一个使用 `AudioBufferSourceNode` 的完整示例：

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

fetch('path/to/audio/file.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        const source = audioContext.createBufferSource();
        source.buffer = buffer;

        // 调度音频在2秒后播放
        source.start(audioContext.currentTime + 2);
        
        // 连接到音频上下文的目标（如扬声器）
        source.connect(audioContext.destination);
    })
    .catch(error => console.error('Error with decoding audio data', error));
```

## 说明
- **常见问题**：确保音频文件路径正确，并且音频文件格式被浏览器支持（如 MP3、WAV 等）。
- **调度精度**：虽然 `AudioScheduledSourceNode` 提供了调度能力，但实际播放时间可能会受到系统性能和其他因素的影响。
- **生命周期管理**：在调用 `start()` 方法后，音频节点会开始播放，确保在播放完毕后处理相关资源。

## 一句话总结
`AudioScheduledSourceNode` 是 Web Audio API 的核心，用于在特定时间调度音频播放，适用于创建专业的音频应用。