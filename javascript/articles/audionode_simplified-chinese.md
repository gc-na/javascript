<!--
Meta Description: # AudioNode：JavaScript 中的音频节点 ## 概述 AudioNode 是 Web Audio API 中的一个核心接口，允许开发者创建复杂的音频处理和合成应用程序。它代表了音频图中的基本构建块，提供了音频信号的处理和传输功能。 ## 文档 ### 目的 AudioNode 旨在...
Meta Keywords: audiocontext, gainnode, audionode, const, connect
-->

# AudioNode：JavaScript 中的音频节点

## 概述
AudioNode 是 Web Audio API 中的一个核心接口，允许开发者创建复杂的音频处理和合成应用程序。它代表了音频图中的基本构建块，提供了音频信号的处理和传输功能。

## 文档
### 目的
AudioNode 旨在提供一种灵活的方式来处理音频信号，使开发者能够创建、连接和操作音频流。它可以用来实现音效、音频合成、以及其他多种音频处理功能。

### 用法
AudioNode 本身是一个抽象类，不能直接实例化。相反，开发者可以使用其子类，如 `GainNode`、`OscillatorNode`、`ScriptProcessorNode` 等，来实现具体的音频处理功能。每个 AudioNode 都可以连接到其他节点，形成音频处理图。

### 详细信息
- **属性**
  - `context`：返回与该节点相关联的 AudioContext。
  - `numberOfInputs`：返回节点的输入数量。
  - `numberOfOutputs`：返回节点的输出数量。
  
- **方法**
  - `connect(destinationNode)`：连接音频节点到目标节点。
  - `disconnect(destinationNode)`：断开与目标节点的连接。

## 示例
### 创建一个简单的音频节点
```javascript
// 创建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 创建一个振荡器节点
const oscillator = audioContext.createOscillator();

// 设置振荡器参数
oscillator.type = 'sine'; // 振荡器类型
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 音符频率

// 创建增益节点
const gainNode = audioContext.createGain();
gainNode.gain.setValueAtTime(0.5, audioContext.currentTime); // 设置音量

// 连接节点
oscillator.connect(gainNode);
gainNode.connect(audioContext.destination);

// 启动振荡器
oscillator.start();
```

### 连接多个节点
```javascript
// 创建多个节点并连接
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator1 = audioContext.createOscillator();
const oscillator2 = audioContext.createOscillator();
const gainNode = audioContext.createGain();

oscillator1.frequency.setValueAtTime(440, audioContext.currentTime); // A4
oscillator2.frequency.setValueAtTime(550, audioContext.currentTime); // C#5

oscillator1.connect(gainNode);
oscillator2.connect(gainNode);
gainNode.connect(audioContext.destination);

oscillator1.start();
oscillator2.start();
```

## 说明
- **常见问题**
  - **无法播放音频**：确保用户与页面的交互触发了 AudioContext 的创建，因为大多数浏览器出于安全原因，需要用户交互才能播放音频。
  - **节点连接顺序**：确保节点按正确的顺序连接，错误的连接可能导致无声或音频处理不当。

- **注意事项**
  - AudioNode 是非阻塞的，多个节点可以并行处理音频。
  - 记得在不需要时调用 `disconnect()` 方法，以释放资源。

## 一句话总结
AudioNode 是 Web Audio API 的基本构建块，用于创建和处理音频信号。