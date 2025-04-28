<!--
Meta Description: # OscillatorNode：JavaScript中音频合成的关键组件 ## 概述 `OscillatorNode` 是 Web Audio API 中的一个重要接口，主要用于生成周期性波形的音频信号。它可以通过不同的波形类型（如正弦波、方波、三角波和锯齿波）创建音频效果，广泛应用于音乐合成和音...
Meta Keywords: oscillatornode, audiocontext, oscillator, when, frequency
-->

# OscillatorNode：JavaScript中音频合成的关键组件

## 概述
`OscillatorNode` 是 Web Audio API 中的一个重要接口，主要用于生成周期性波形的音频信号。它可以通过不同的波形类型（如正弦波、方波、三角波和锯齿波）创建音频效果，广泛应用于音乐合成和音效设计。

## 文档

### 目的
`OscillatorNode` 允许开发者生成合成音频信号，支持实时音频处理和动态变化，是音频应用程序和游戏开发中常用的工具。

### 用法
要创建一个 `OscillatorNode`，首先需要初始化一个 `AudioContext`，然后利用该上下文的 `createOscillator()` 方法生成一个振荡器节点。以下是 `OscillatorNode` 的基本属性和方法：

- **属性**:
  - `frequency`：表示振荡器的频率，单位为赫兹（Hz）。
  - `type`：表示振荡器的波形类型，可以是以下几种：
    - `sine`
    - `square`
    - `triangle`
    - `sawtooth`

- **方法**:
  - `start([when])`：开始振荡器的生成，`when` 可选参数表示延迟开始的时间。
  - `stop([when])`：停止振荡器的生成，`when` 可选参数表示延迟停止的时间。

### 示例
以下是 `OscillatorNode` 的基本用法示例：

```javascript
// 创建一个音频上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 创建振荡器节点
const oscillator = audioContext.createOscillator();

// 设置振荡器属性
oscillator.type = 'sine'; // 波形类型
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4音符

// 连接振荡器到音频上下文的目标
oscillator.connect(audioContext.destination);

// 启动振荡器
oscillator.start();

// 5秒后停止振荡器
oscillator.stop(audioContext.currentTime + 5);
```

### 说明
在使用 `OscillatorNode` 时，请注意以下几点：

- **频率范围**：`frequency` 属性的值应在 0 到 20000 Hz 之间，超出此范围可能导致不稳定的音效。
- **波形类型**：选择合适的波形类型可以影响音色，了解不同波形的特性有助于创造更丰富的音效。
- **音频上下文**：在使用 `OscillatorNode` 之前，确保 `AudioContext` 已经正确创建并处于“运行”状态。

## 一句话总结
`OscillatorNode` 是 Web Audio API 中用于生成周期性音频信号的核心组件，支持多种波形和频率设置。