<!--
Meta Description: # AudioScheduledSourceNode：JavaScript中的音頻調度源節點 ## 概述 AudioScheduledSourceNode 是 Web Audio API 中的一個重要接口，主要用於處理音頻的播放和調度。它允許開發者在特定的時間點播放音頻，並提供多種音頻控制功能。 #...
Meta Keywords: audiocontext, audioscheduledsourcenode, audio, audiobuffersourcenode, source
-->

# AudioScheduledSourceNode：JavaScript中的音頻調度源節點

## 概述
AudioScheduledSourceNode 是 Web Audio API 中的一個重要接口，主要用於處理音頻的播放和調度。它允許開發者在特定的時間點播放音頻，並提供多種音頻控制功能。

## 文檔
### 目的
AudioScheduledSourceNode 的主要目的是提供一個音頻源，該源可以被調度到特定的時間點播放，並支持多種音效操作。它的子類型包括 `AudioBufferSourceNode` 和 `ConstantSourceNode`。

### 用法
要使用 AudioScheduledSourceNode，您通常會先創建一個 `AudioContext`，然後根據需要創建相應的音頻源節點。以下是創建和使用 `AudioBufferSourceNode` 的基本步驟：

1. 創建一個 `AudioContext` 實例。
2. 創建一個 `AudioBufferSourceNode`。
3. 設置音頻緩衝區。
4. 調用 `start()` 方法來播放音頻。

### 詳細信息
- **屬性**：
  - `playbackState`：指示音頻源的播放狀態。
- **方法**：
  - `start(when)`：在指定時間開始播放音頻。
  - `stop(when)`：在指定時間停止播放音頻。

## 示例
以下是如何使用 `AudioBufferSourceNode` 的基本示例：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 載入音頻檔案
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // 創建音頻源
    const source = audioContext.createBufferSource();
    source.buffer = buffer; // 設置音頻緩衝區
    source.connect(audioContext.destination); // 連接到輸出
    
    // 在指定時間播放音頻
    source.start(0);
  })
  .catch(error => console.error('Error with decoding audio data', error));
```

## 解釋
使用 AudioScheduledSourceNode 時，開發者常見的陷阱包括：
- 在沒有正確設置 `AudioContext` 的情況下嘗試播放音頻。
- 忘記在播放之前設置音頻緩衝區。
- 在 `AudioScheduledSourceNode` 被調用後再次嘗試開始播放，因為一旦播放結束，這些節點將無法重複使用。

## 一句總結
AudioScheduledSourceNode 是 Web Audio API 中用於音頻調度和播放的關鍵接口，提供了靈活的音頻控制能力。