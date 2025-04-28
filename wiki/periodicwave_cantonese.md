<!--
Meta Description: # PeriodicWave：JavaScript 中的波形生成器 ## 概述 PeriodicWave 是 Web Audio API 的一部分，允許開發者生成和使用周期性波形，這對於音頻合成和音效設計非常重要。它提供了一種簡單的方法來創建正弦波、方波、鋸齒波等各種波形。 ## 文檔 ### 目的...
Meta Keywords: periodicwave, audiocontext, real, const, imag
-->

# PeriodicWave：JavaScript 中的波形生成器

## 概述
PeriodicWave 是 Web Audio API 的一部分，允許開發者生成和使用周期性波形，這對於音頻合成和音效設計非常重要。它提供了一種簡單的方法來創建正弦波、方波、鋸齒波等各種波形。

## 文檔
### 目的
PeriodicWave 的主要目的是生成可用於音頻合成的周期性波形。這些波形可以用來創建音頻上下文中的音頻源，並且可以通過不同的參數進行調整，以達到所需的音效。

### 使用方法
要使用 PeriodicWave，首先需要創建一個 AudioContext 的實例，然後通過該上下文來創建 PeriodicWave 對象。其基本語法如下：

```javascript
const audioContext = new AudioContext();
const periodicWave = audioContext.createPeriodicWave(real, imag);
```

其中 `real` 和 `imag` 是浮點數數組，分別代表波形的實部和虛部。

### 詳細信息
- **real**：一個浮點數數組，定義波形的實部。長度應為 N + 1，N 是波的頻率數。
- **imag**：一個浮點數數組，定義波形的虛部。長度應與 `real` 相同，或者可以省略，預設為全零。

### 重要屬性
- `periodicWave.real`: 獲取波形的實部。
- `periodicWave.imag`: 獲取波形的虛部。

## 示例
以下是如何創建一個簡單的正弦波的示例：

```javascript
const audioContext = new AudioContext();
const real = new Float32Array([0, 1]); // 只包含一個頻率
const imag = new Float32Array([0]); // 沒有虛部
const periodicWave = audioContext.createPeriodicWave(real, imag);

const oscillator = audioContext.createOscillator();
oscillator.setPeriodicWave(periodicWave);
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 設置頻率為440Hz
oscillator.connect(audioContext.destination);
oscillator.start();
```

## 解釋
在使用 PeriodicWave 時，有幾個常見的陷阱需要注意：
1. **數組長度**：確保 `real` 和 `imag` 數組的長度正確，特別是 `real` 數組的長度必須為 N + 1。
2. **音頻上下文**：在創建 PeriodicWave 之前，必須初始化 AudioContext，否則會報錯。
3. **異步操作**：音頻的播放需要在用戶交互後進行，否則可能會因瀏覽器的自動播放策略而被阻止。

## 總結
PeriodicWave 是一個強大的工具，可以幫助開發者在 JavaScript 中生成和控制周期性波形，為音頻合成提供靈活性和創造性。