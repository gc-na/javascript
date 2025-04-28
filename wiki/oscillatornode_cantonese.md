<!--
Meta Description: # OscillatorNode：JavaScript 音頻處理的關鍵組件 ## 簡介 OscillatorNode 是 Web Audio API 中的一個重要組件，用於生成周期性波形的音頻信號。它可以用來創建合成音樂或音效，並在網頁應用中提供動態音頻功能。 ## 文檔 ### 目的 Oscill...
Meta Keywords: oscillator, oscillatornode, audiocontext, start, stop
-->

# OscillatorNode：JavaScript 音頻處理的關鍵組件

## 簡介
OscillatorNode 是 Web Audio API 中的一個重要組件，用於生成周期性波形的音頻信號。它可以用來創建合成音樂或音效，並在網頁應用中提供動態音頻功能。

## 文檔
### 目的
OscillatorNode 主要用於生成各種波形的音頻信號，例如正弦波、方波、三角波和鋸齒波。開發者可以利用這些波形來創建聲音，進行音頻合成或音效處理。

### 使用方法
1. **創建 AudioContext**：首先需要創建一個 AudioContext 以便使用 Web Audio API。
2. **創建 OscillatorNode**：使用 `audioContext.createOscillator()` 方法來創建一個 oscillator 實例。
3. **設置波形類型**：使用 `oscillator.type` 屬性設置波形類型（例如 "sine", "square", "sawtooth", "triangle"）。
4. **設置頻率**：使用 `oscillator.frequency.value` 設置音頻頻率（以赫茲為單位）。
5. **連接至音頻輸出**：使用 `oscillator.connect(audioContext.destination)` 將 OscillatorNode 連接到音頻輸出。
6. **開始和停止**：使用 `oscillator.start()` 開始播放，使用 `oscillator.stop()` 停止播放。

### 詳細資訊
- **屬性**：
  - `type`: 定義波形的類型，可選擇 "sine", "square", "sawtooth", "triangle"。
  - `frequency`: 一個 AudioParam 用於設置音頻的頻率，默認為 440Hz。
  
- **方法**：
  - `start(when)`: 開始播放聲音，`when` 參數可選，表示延遲時間。
  - `stop(when)`: 停止播放聲音，`when` 參數可選，表示延遲時間。

## 範例
### 基本用法範例
```javascript
// 創建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 OscillatorNode
const oscillator = audioContext.createOscillator();

// 設置波形類型和頻率
oscillator.type = 'sine'; // 正弦波
oscillator.frequency.value = 440; // 440Hz

// 連接至音頻輸出
oscillator.connect(audioContext.destination);

// 開始播放
oscillator.start();

// 停止播放（在 2 秒後）
setTimeout(() => {
    oscillator.stop();
}, 2000);
```

## 解釋
在使用 OscillatorNode 時，開發者需要注意以下幾點：
- **頻率範圍**：不同波形的頻率範圍可能會影響音質，選擇合適的頻率是關鍵。
- **連接問題**：確保在開始播放之前已經正確連接到音頻輸出，否則不會聽到聲音。
- **重複使用**：每次使用 `start()` 和 `stop()` 方法後，OscillatorNode 將無法再次使用，需要創建新的實例。

## 一句話總結
OscillatorNode 是 Web Audio API 的一個強大工具，用於生成多種波形的音頻信號，實現音頻合成和效果處理。