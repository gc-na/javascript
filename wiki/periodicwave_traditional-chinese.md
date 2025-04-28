<!--
Meta Description: # PeriodicWave：JavaScript 中的週期波形生成 ## 概述 `PeriodicWave` 是 Web Audio API 中的一個功能，允許開發者生成和操作週期性波形。這種波形可以用於創建合成音效，特別是在音樂和聲音設計中非常有用。 ## 文檔 ### 目的 `Periodic...
Meta Keywords: periodicwave, audiocontext, const, new, real
-->

# PeriodicWave：JavaScript 中的週期波形生成

## 概述
`PeriodicWave` 是 Web Audio API 中的一個功能，允許開發者生成和操作週期性波形。這種波形可以用於創建合成音效，特別是在音樂和聲音設計中非常有用。

## 文檔
### 目的
`PeriodicWave` 主要用於創建自定義的週期波形，這些波形可以用於音頻合成器的音源。它提供了靈活性來設計各種音效，從簡單的正弦波到複雜的聲音。

### 使用方法
要使用 `PeriodicWave`，首先需創建一個音頻上下文 (`AudioContext`)。然後可以利用 `createPeriodicWave` 方法來生成波形。生成後，可以將其分配給音頻合成器的音源，並進行播放。

### 詳細說明
```javascript
const audioContext = new AudioContext();
const real = new Float32Array([0, 1, 0, 0]); // 實部數據
const imag = new Float32Array([0, 0, 1, 0]); // 虛部數據
const periodicWave = audioContext.createPeriodicWave(real, imag);
```

- **real**：一個浮點數陣列，表示波形的實部。
- **imag**：一個浮點數陣列，表示波形的虛部。
- **createPeriodicWave**：這個方法會返回一個新的 `PeriodicWave` 對象。

## 範例
以下是一個簡單的範例，展示如何使用 `PeriodicWave` 生成並播放一個自定義的波形：

```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
const real = new Float32Array([0, 1, 0, 0]); // 實部
const imag = new Float32Array([0, 0, 1, 0]); // 虛部
const periodicWave = audioContext.createPeriodicWave(real, imag);

oscillator.setPeriodicWave(periodicWave);
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 設定頻率為440Hz
oscillator.connect(audioContext.destination);
oscillator.start();
```

## 解釋
在使用 `PeriodicWave` 時，開發者需要注意以下幾點：
- **數據長度**：實部和虛部數據的長度必須相等，否則將會引發錯誤。
- **音頻上下文狀態**：在使用 `PeriodicWave` 之前，必須確保音頻上下文已經處於運行狀態。
- **性能考量**：複雜的波形可能會影響性能，特別是在需要大量同時播放的情況下。

## 總結
`PeriodicWave` 是一個強大的工具，可用於生成和操作自定義的週期波形，為音頻合成提供了極大的靈活性和創造性。