<!--
Meta Description: # WaveShaperNode：JavaScript 中的音頻波形塑形節點 ## 概述 WaveShaperNode 是 Web Audio API 中的一個核心組件，用於對音頻信號進行波形塑形處理。它能夠改變音頻信號的波形，創造出獨特的音效，並廣泛應用於音頻處理和合成中。 ## 文件說明 ###...
Meta Keywords: waveshapernode, audiocontext, const, oscillator, curve
-->

# WaveShaperNode：JavaScript 中的音頻波形塑形節點

## 概述
WaveShaperNode 是 Web Audio API 中的一個核心組件，用於對音頻信號進行波形塑形處理。它能夠改變音頻信號的波形，創造出獨特的音效，並廣泛應用於音頻處理和合成中。

## 文件說明
### 目的
WaveShaperNode 的主要目的是對音頻信號進行非線性處理，從而創造出各種音效，如失真（distortion）、過載（overdrive）等。

### 使用方法
要使用 WaveShaperNode，首先需要創建一個音頻上下文（AudioContext），然後使用該上下文的 `createWaveShaper()` 方法來實例化 WaveShaperNode。接著，可以設置波形數據，以定義如何塑形音頻信號。

### 詳細內容
```javascript
// 創建音頻上下文
const audioContext = new AudioContext();

// 創建 WaveShaperNode
const waveShaperNode = audioContext.createWaveShaper();

// 設置波形
waveShaperNode.curve = new Float32Array([0, 0.5, 1, 0.5, 0]);
waveShaperNode.oversample = '4x'; // 可以選擇 'none', '2x', '4x'

// 將 WaveShaperNode 連接到音頻上下文的目的地
waveShaperNode.connect(audioContext.destination);
```

## 範例
以下是如何使用 WaveShaperNode 的基本範例：

### 範例 1：簡單的波形塑形
```javascript
const audioContext = new AudioContext();
const waveShaperNode = audioContext.createWaveShaper();

waveShaperNode.curve = new Float32Array([0, 1, 1, 0]); // 簡單的波形定義
waveShaperNode.oversample = 'none';

const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 音符的頻率

// 連接音頻路徑
oscillator.connect(waveShaperNode);
waveShaperNode.connect(audioContext.destination);

// 開始播放
oscillator.start();
```

### 範例 2：使用複雜波形
```javascript
const audioContext = new AudioContext();
const waveShaperNode = audioContext.createWaveShaper();

const curve = new Float32Array(256);
for (let i = 0; i < curve.length; ++i) {
    const x = (i * 2) / curve.length - 1; // 從 -1 到 1 的範圍
    curve[i] = (x < 0) ? Math.pow(x, 2) : Math.sqrt(x); // 定義非線性
}
waveShaperNode.curve = curve;
waveShaperNode.oversample = '4x';

const oscillator = audioContext.createOscillator();
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 音符的頻率

oscillator.connect(waveShaperNode);
waveShaperNode.connect(audioContext.destination);
oscillator.start();
```

## 解釋
在使用 WaveShaperNode 時，開發者應注意以下幾點：
- **波形數據**：波形數據的長度和內容會直接影響音效的質量和特徵。確保選擇合適的數據來達到所需的效果。
- **oversample 屬性**：該屬性可以提高音質，但會增加 CPU 負擔。根據應用場景選擇合適的設定。
- **連接順序**：確保音頻節點的連接順序正確，以避免出現意外的音效。

## 總結
WaveShaperNode 是一個強大的工具，使得 JavaScript 開發者能夠創造多樣化的音頻效果，特別是在音頻合成和處理方面。