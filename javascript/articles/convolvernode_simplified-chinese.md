<!--
Meta Description: # ConvolverNode：JavaScript 音频处理中的卷积节点 ## 概述 ConvolverNode 是 Web Audio API 中的一个重要组件，允许开发者对音频信号进行卷积处理，模拟不同的声学环境。通过使用 ConvolverNode，开发者能够为音频添加混响效果，从而增强音频...
Meta Keywords: audiocontext, convolvernode, response, then, convolver
-->

# ConvolverNode：JavaScript 音频处理中的卷积节点

## 概述
ConvolverNode 是 Web Audio API 中的一个重要组件，允许开发者对音频信号进行卷积处理，模拟不同的声学环境。通过使用 ConvolverNode，开发者能够为音频添加混响效果，从而增强音频的空间感和丰富度。

## 文档
### 目的
ConvolverNode 的主要目的是将一个音频信号与一个脉冲响应（Impulse Response，IR）进行卷积，生成具有特定空间特征的音频输出。

### 用法
要使用 ConvolverNode，首先需要创建一个音频上下文（AudioContext），然后创建一个 ConvolverNode 实例，并加载一个脉冲响应。最后，将音频源连接到 ConvolverNode，最后再连接到目标输出（如扬声器）。

### 详细说明
- **创建音频上下文：**
  ```javascript
  const audioContext = new AudioContext();
  ```

- **创建 ConvolverNode：**
  ```javascript
  const convolver = audioContext.createConvolver();
  ```

- **加载脉冲响应：**
  脉冲响应通常是一个音频文件，可以通过 XMLHttpRequest 或 Fetch API 加载：
  ```javascript
  fetch('path/to/impulse-response.wav')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
      convolver.buffer = buffer;
    });
  ```

- **连接音频源：**
  ```javascript
  const source = audioContext.createBufferSource();
  source.buffer = audioBuffer; // 加载的音频数据
  source.connect(convolver);
  convolver.connect(audioContext.destination);
  ```

## 示例
以下是一个简单的示例，展示如何使用 ConvolverNode 创建一个带有混响效果的音频播放器：

```javascript
const audioContext = new AudioContext();
const convolver = audioContext.createConvolver();

fetch('path/to/impulse-response.wav')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    convolver.buffer = buffer;

    const source = audioContext.createBufferSource();
    fetch('path/to/audio-file.mp3')
      .then(response => response.arrayBuffer())
      .then(data => audioContext.decodeAudioData(data))
      .then(audioBuffer => {
        source.buffer = audioBuffer;
        source.connect(convolver);
        convolver.connect(audioContext.destination);
        source.start();
      });
  });
```

## 说明
- **常见问题：**
  - 确保脉冲响应文件格式正确，并且可以被解码。
  - 在音频上下文未处于“运行”状态时，无法播放音频。需要使用 `audioContext.resume()` 来恢复音频上下文。
  
- **注意事项：**
  - ConvolverNode 的性能可能受到脉冲响应长度的影响，较长的脉冲响应可能导致更高的 CPU 使用率。
  - 在使用 ConvolverNode 时，建议使用较短的脉冲响应以保持实时性能。

## 一句话总结
ConvolverNode 是 Web Audio API 中用于音频卷积处理的节点，能够为音频信号添加混响效果，模拟真实的声学环境。