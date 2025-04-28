<!--
Meta Description: # AudioBufferSourceNode：JavaScript 中的音頻播放節點 ## 摘要 `AudioBufferSourceNode` 是 Web Audio API 中的一個重要接口，允許開發者從內存中播放音頻數據。它能夠處理音頻緩衝區並提供多種控制選項，適用於各種音頻應用程序。 ##...
Meta Keywords: audiobuffersourcenode, audiocontext, source, audio, buffer
-->

# AudioBufferSourceNode：JavaScript 中的音頻播放節點

## 摘要
`AudioBufferSourceNode` 是 Web Audio API 中的一個重要接口，允許開發者從內存中播放音頻數據。它能夠處理音頻緩衝區並提供多種控制選項，適用於各種音頻應用程序。

## 文檔
`AudioBufferSourceNode` 是一個音頻節點，專門用於播放已經加載到 `AudioBuffer` 中的音頻數據。它可以用於創建高品質的音頻播放效果，並支持重複播放、音量控制等功能。

### 目的
`AudioBufferSourceNode` 的主要目的是提供一種簡便的方法來播放聲音，特別是在需要從緩衝區中重複播放音頻時。它的設計兼顧了靈活性和高效能。

### 使用方式
要使用 `AudioBufferSourceNode`，你需要先創建一個 `AudioContext`，然後從音頻文件或其它來源加載音頻數據到 `AudioBuffer` 中。接著，使用 `createBufferSource()` 方法創建一個 `AudioBufferSourceNode` 實例，並將音頻數據連接到音頻上下文的輸出。

### 詳細信息
- **屬性**：
  - `buffer`: 設置要播放的 `AudioBuffer`。
  - `loop`: 設置是否重複播放。
  - `playbackRate`: 音頻播放速度的倍數。

- **方法**：
  - `start()`: 開始播放音頻，支持指定開始時間和結束時間。
  - `stop()`: 停止音頻播放，支持指定停止時間。

## 範例
以下是一個基本的使用示例：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 加載音頻文件
fetch('audio-file-url.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // 創建音頻源節點
    const source = audioContext.createBufferSource();
    source.buffer = buffer; // 設置音頻緩衝區
    source.loop = true; // 設置為循環播放
    source.connect(audioContext.destination); // 連接到輸出
    source.start(0); // 開始播放
  })
  .catch(error => console.error('Error with decoding audio data' + error));
```

## 解釋
使用 `AudioBufferSourceNode` 時，開發者應注意以下幾點：
- **重複播放**：如果需要重複播放，請確保設置 `loop` 屬性為 `true`。
- **開始與停止**：每個 `AudioBufferSourceNode` 只能播放一次。如果需要再次播放，必須創建新的實例。
- **異步處理**：音頻數據的加載和解碼是異步的，因此務必處理相關的 Promise。

## 一句話總結
`AudioBufferSourceNode` 是 Web Audio API 中用於播放音頻緩衝區的節點，提供靈活的音頻控制選項。