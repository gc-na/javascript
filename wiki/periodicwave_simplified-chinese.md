<!--
Meta Description: # PeriodicWave：JavaScript 中的周期波形 ## 概述 `PeriodicWave` 是 Web Audio API 中用于创建周期性波形的一个重要特性。它允许开发者生成自定义波形，以用于声音合成和音频处理。 ## 文档 ### 目的 `PeriodicWave` 的主要目的是...
Meta Keywords: periodicwave, audiocontext, oscillator, real, imag
-->

# PeriodicWave：JavaScript 中的周期波形

## 概述
`PeriodicWave` 是 Web Audio API 中用于创建周期性波形的一个重要特性。它允许开发者生成自定义波形，以用于声音合成和音频处理。

## 文档
### 目的
`PeriodicWave` 的主要目的是生成周期性波形，以便在音频合成中使用。通过定义波形的幅度和相位，开发者可以创建各种复杂的音频效果。

### 用法
要使用 `PeriodicWave`，首先需要创建一个音频上下文对象。然后，可以通过 `AudioContext.createPeriodicWave` 方法来实例化一个周期波形。

### 详细信息
- **构造函数**：`PeriodicWave` 通过 `AudioContext.createPeriodicWave(real, imag)` 方法创建。
  - `real`：一个 `Float32Array`，定义波形的实部。
  - `imag`：一个 `Float32Array`，定义波形的虚部（可选，默认为零）。
  
- **属性**：
  - `real`：返回波形的实部数组。
  - `imag`：返回波形的虚部数组。

- **使用场景**：
  - 音乐合成：创建复杂的乐器声音。
  - 音频效果：生成不同的音效和过滤器。

## 示例
以下是使用 `PeriodicWave` 创建简单波形的示例代码：

```javascript
// 创建音频上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 定义实部和虚部
const real = new Float32Array([0, 1, 0.5, 0.25]);
const imag = new Float32Array([0, 0, 0, 0]);

// 创建周期波形
const periodicWave = audioContext.createPeriodicWave(real, imag);

// 创建振荡器并连接到音频上下文
const oscillator = audioContext.createOscillator();
oscillator.setPeriodicWave(periodicWave);
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 设置频率为440Hz

// 播放音频
oscillator.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 2); // 播放2秒
```

## 说明
在使用 `PeriodicWave` 时，有几个常见的问题需要注意：
- **性能**：复杂的波形可能会导致性能下降，特别是在实时音频处理中。
- **频率范围**：确保设置的频率在适当的范围内，以避免音频失真。
- **数组长度**：实部和虚部的数组长度应相同，且应为非负值。

## 一句话总结
`PeriodicWave` 是 Web Audio API 中的一个功能，用于生成自定义的周期性波形，实现音频合成和处理。