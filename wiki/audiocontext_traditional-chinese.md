<!--
Meta Description: # JavaScript 中的 AudioContext：音頻處理的核心 ## 概述 AudioContext 是 Web Audio API 的一部分，用於處理和播放音頻。它提供了一個環境來創建和操作音頻信號，並為音頻應用程式和遊戲開發者提供強大的工具。 ## 文檔 ### 目的 AudioCon...
Meta Keywords: audiocontext, source, gainnode, const, buffer
-->

# JavaScript 中的 AudioContext：音頻處理的核心

## 概述
AudioContext 是 Web Audio API 的一部分，用於處理和播放音頻。它提供了一個環境來創建和操作音頻信號，並為音頻應用程式和遊戲開發者提供強大的工具。

## 文檔
### 目的
AudioContext 主要用於創建音頻圖形，並管理音頻層的播放、分析和處理。它是所有音頻操作的起點，支持多種音頻源（如音頻文件、麥克風輸入等）和效果處理（如濾波器、增益等）。

### 用法
要使用 AudioContext，首先需要創建一個實例：
```javascript
const audioContext = new AudioContext();
```

創建後，可以使用這個上下文來加載音頻檔案、創建音頻節點並將它們連接在一起。以下是一些常用的音頻節點：
- **AudioBufferSourceNode**：用於播放音頻檔案。
- **GainNode**：用於控制音量。
- **AnalyserNode**：用於分析音頻頻譜。

### 詳細信息
- **屬性**：
  - `sampleRate`：音頻上下文的取樣率（每秒樣本數）。
  - `state`：當前狀態（如 "suspended"、"running" 或 "closed"）。
  
- **方法**：
  - `suspend()`：暫停音頻上下文。
  - `resume()`：恢復音頻上下文。
  - `close()`：關閉音頻上下文並釋放資源。

## 範例
### 基本用法
下面的示例展示了如何創建一個 AudioContext 並播放一個基本的音頻檔案：

```javascript
const audioContext = new AudioContext();

fetch('path/to/audio.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const source = audioContext.createBufferSource();
    source.buffer = buffer;
    source.connect(audioContext.destination);
    source.start(0);
  })
  .catch(error => console.error('Error with decoding audio data', error));
```

### 使用 GainNode 調整音量
```javascript
const gainNode = audioContext.createGain();
gainNode.gain.value = 0.5; // 將音量調整為 50%

const source = audioContext.createBufferSource();
source.buffer = buffer;
source.connect(gainNode);
gainNode.connect(audioContext.destination);
source.start(0);
```

## 解釋
- **常見錯誤**：
  - 在創建 AudioContext 前，某些瀏覽器可能需要用戶互動（如點擊或觸摸）。
  - 確保音頻檔案格式瀏覽器支持，如 MP3 或 WAV。

- **注意事項**：
  - AudioContext 的實例只能在同一個域下使用（跨域請求需設置 CORS）。
  - 使用 AudioContext 時，請注意管理資源，以免造成內存洩漏。

## 一句話總結
AudioContext 是 Web Audio API 的基礎，提供音頻處理和播放的強大功能。