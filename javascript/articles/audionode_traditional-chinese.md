<!--
Meta Description: # AudioNode：JavaScript 中的音頻節點 ## 簡介 `AudioNode` 是 Web Audio API 的核心組件之一，允許開發者創建和操作音頻流。它是所有音頻處理和合成的基本單位，能夠用於創建音效、音樂和其他音頻應用。 ## 文檔 `AudioNode` 代表音頻處理圖中的...
Meta Keywords: audiocontext, audionode, gainnode, javascript, const
-->

# AudioNode：JavaScript 中的音頻節點

## 簡介
`AudioNode` 是 Web Audio API 的核心組件之一，允許開發者創建和操作音頻流。它是所有音頻處理和合成的基本單位，能夠用於創建音效、音樂和其他音頻應用。

## 文檔
`AudioNode` 代表音頻處理圖中的一個節點，每個節點都可以是音源、音效處理器或輸出。Web Audio API 中的所有音頻節點都繼承自 `AudioNode`，包括 `GainNode`、`OscillatorNode` 和 `ScriptProcessorNode` 等。

### 目的
`AudioNode` 的主要目的在於提供一個統一的接口來控制音頻流的生成和處理。它能夠支持各種音頻操作，如增益調整、音調合成、音效應用等。

### 用法
要使用 `AudioNode`，通常需要先創建一個 `AudioContext`，然後通過該上下文創建具體的音頻節點。以下是創建和使用 `AudioNode` 的基本步驟：

1. 創建 `AudioContext`：
   ```javascript
   const audioContext = new AudioContext();
   ```

2. 創建具體的音頻節點，如 `GainNode`：
   ```javascript
   const gainNode = audioContext.createGain();
   ```

3. 連接節點：
   ```javascript
   gainNode.connect(audioContext.destination);
   ```

## 範例
以下是使用 `GainNode` 音頻節點的簡單示例：

```javascript
const audioContext = new AudioContext();
const gainNode = audioContext.createGain();
gainNode.gain.value = 0.5; // 設定增益為 0.5

const oscillator = audioContext.createOscillator();
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 設定頻率為 440Hz

oscillator.connect(gainNode); // 將振盪器連接到增益節點
gainNode.connect(audioContext.destination); // 將增益節點連接到輸出

oscillator.start(); // 開始播放
```

## 解釋
在使用 `AudioNode` 時，有幾個常見的陷阱需要注意：

- **音頻上下文的狀態**：`AudioContext` 必須在用戶互動後創建（例如點擊事件），否則可能無法正常運行。
- **節點連接**：必須正確連接所有節點，否則音頻將無法播放。
- **資源管理**：確保在不需要音頻時停止和釋放音頻資源，避免內存洩漏。

## 一句話總結
`AudioNode` 是 Web Audio API 中的基本組件，用於創建和處理音頻流，是音頻應用開發的核心。