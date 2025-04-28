<!--
Meta Description: # OscillatorNode：JavaScript 中的音頻振盪器節點 ## 摘要 OscillatorNode 是 Web Audio API 中的一個重要組件，用於生成周期性波形的音頻信號，適合用於創建音樂和音效。 ## 文檔 ### 目的 OscillatorNode 允許開發者生成不同類...
Meta Keywords: audiocontext, oscillatornode, oscillator, when, start
-->

# OscillatorNode：JavaScript 中的音頻振盪器節點

## 摘要
OscillatorNode 是 Web Audio API 中的一個重要組件，用於生成周期性波形的音頻信號，適合用於創建音樂和音效。

## 文檔
### 目的
OscillatorNode 允許開發者生成不同類型的音頻波形，包括正弦波、方波、三角波和鋸齒波。它是音頻合成的重要工具，能夠用於創建音樂、音效或任何需要合成音頻的應用。

### 使用
要使用 OscillatorNode，首先需要創建一個 AudioContext 實例。然後通過 AudioContext 的 `createOscillator()` 方法創建一個 OscillatorNode。可以設置波形類型和頻率，並使用 `start()` 方法開始播放。

### 詳細信息
- **屬性**：
  - `type`: 設定波形類型，可選值有 `"sine"`、`"square"`、`"triangle"` 和 `"sawtooth"`。
  - `frequency`: 一個 `AudioParam`，用於設置振盪器的頻率，單位為赫茲（Hz）。
  - `detune`: 一個 `AudioParam`，用於微調音高，單位為分（cents）。

- **方法**：
  - `start(when)`: 開始振盪器。`when` 參數可選，指定開始播放的時間。
  - `stop(when)`: 停止振盪器。`when` 參數可選，指定停止播放的時間。

## 示例
```javascript
// 創建一個 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建一個振盪器節點
const oscillator = audioContext.createOscillator();

// 設置波形類型和頻率
oscillator.type = 'sine'; // 可選 'sine', 'square', 'triangle', 'sawtooth'
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 設置頻率為 440 Hz（A4音）

// 連接到音頻上下文的輸出
oscillator.connect(audioContext.destination);

// 開始播放
oscillator.start();

// 停止播放
setTimeout(() => {
    oscillator.stop();
}, 2000); // 2秒後停止
```

## 解釋
使用 OscillatorNode 時的一些常見注意事項：
- 確保在用戶交互後才創建 AudioContext，以避免瀏覽器的自動播放限制。
- 設定頻率時，使用 `setValueAtTime` 方法可以平滑變化，不會造成突變。
- 停止振盪器時，確保在 `stop()` 方法被調用後不再使用該振盪器，因為它將無法再播放。

## 一句總結
OscillatorNode 是 Web Audio API 中用於生成音頻波形的核心組件，適合音頻合成和實時音效創建。