<!--
Meta Description: # ConstantSourceNode：JavaScript 中的常量音源节点 ## 概述 `ConstantSourceNode` 是 Web Audio API 中的一个接口，用于创建生成恒定信号的音源节点。它通常用于生成持续的音频信号，如测试音频和振荡器。 ## 文档 `ConstantSo...
Meta Keywords: constantsourcenode, audiocontext, constantsource, javascript, const
-->

# ConstantSourceNode：JavaScript 中的常量音源节点

## 概述
`ConstantSourceNode` 是 Web Audio API 中的一个接口，用于创建生成恒定信号的音源节点。它通常用于生成持续的音频信号，如测试音频和振荡器。

## 文档
`ConstantSourceNode` 的主要用途是提供一个恒定的音频信号源。它可以输出一个不断重复的固定值，通常用于调试或作为其他音频处理的基础。以下是 `ConstantSourceNode` 的一些关键特性：

- **创建方式**：通过 `AudioContext` 的 `createConstantSource()` 方法来实例化。
- **输出**：`ConstantSourceNode` 输出一个恒定的音频信号，通常用于音频合成。
- **连接**：可以与其他音频节点连接，如 `GainNode` 或 `AudioDestinationNode`。

### 使用方法
```javascript
// 创建音频上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 创建 ConstantSourceNode
const constantSource = audioContext.createConstantSource();

// 设置输出的常量值（以赫兹为单位）
constantSource.offset.value = 0.5; // 设定音量为 0.5

// 连接到目标节点
constantSource.connect(audioContext.destination);

// 启动 ConstantSourceNode
constantSource.start();
```

## 示例
以下是 `ConstantSourceNode` 的基本用法示例：

### 示例 1：创建并播放恒定信号
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioContext.createConstantSource();
constantSource.offset.value = 0.5; // 设置输出值
constantSource.connect(audioContext.destination); // 连接到音频目的地
constantSource.start(); // 启动音源
```

### 示例 2：停止恒定信号
```javascript
setTimeout(() => {
    constantSource.stop(); // 停止音频输出
}, 5000); // 5秒后停止
```

## 说明
在使用 `ConstantSourceNode` 时，有几个常见的注意事项：

1. **时间控制**：`ConstantSourceNode` 在调用 `start()` 方法后会立即开始输出信号。若需要在未来的某个时间点开始，可以使用 `start(when)` 方法。
   
2. **停止音源**：通过调用 `stop()` 方法来停止音源，注意一旦停止，节点将无法重新启动。

3. **连接限制**：`ConstantSourceNode` 只能连接到一个唯一的目标节点，若需要多次连接，需要创建新的实例。

4. **音频上下文状态**：确保 `AudioContext` 处于“运行”状态，否则音频信号将不会被播放。

## 一句话总结
`ConstantSourceNode` 是 Web Audio API 中用于生成恒定音频信号的节点，广泛应用于音频合成和测试。