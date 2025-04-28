<!--
Meta Description: # AudioBufferSourceNode：JavaScript 音頻處理的核心 ## 概述 `AudioBufferSourceNode` 是 Web Audio API 中的一個接口，用於播放音頻數據。它可以從 `AudioBuffer` 中提取音頻樣本，並透過音頻上下文進行播放，適合用於音...
Meta Keywords: audiocontext, audiobuffersourcenode, source, buffer, error
-->

# AudioBufferSourceNode：JavaScript 音頻處理的核心

## 概述
`AudioBufferSourceNode` 是 Web Audio API 中的一個接口，用於播放音頻數據。它可以從 `AudioBuffer` 中提取音頻樣本，並透過音頻上下文進行播放，適合用於音效、音樂播放器等應用。

## 文檔
### 目的
`AudioBufferSourceNode` 主要用於播放預先加載的音頻數據。它提供了簡單的接口來控制音頻的播放、停止以及音量等屬性。

### 使用方法
要使用 `AudioBufferSourceNode`，您需要先創建一個 `AudioContext`，然後使用 `createBufferSource()` 方法來創建一個音頻源節點。

```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();
```

接下來，您需要將音頻數據加載到 `AudioBuffer` 中，並將其分配給 `AudioBufferSourceNode` 的 `buffer` 屬性。

```javascript
fetch('audio-file.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        source.buffer = buffer;
        source.connect(audioContext.destination);
        source.start(0);
    })
    .catch(error => console.error('Error with fetching audio data:', error));
```

### 詳細信息
- **屬性**：
  - `buffer`: 存儲要播放的音頻數據。
  - `loop`: 一個布林值，決定音頻是否循環播放。
  - `playbackRate`: 控制音頻播放速率，默認值為 1.0。

- **方法**：
  - `start()`: 開始播放音頻，您可以指定播放的開始時間和持續時間。
  - `stop()`: 停止播放音頻。

## 範例
以下是使用 `AudioBufferSourceNode` 播放音頻的基本範例：

```javascript
const audioContext = new AudioContext();

fetch('audio-file.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        const source = audioContext.createBufferSource();
        source.buffer = buffer;
        source.loop = true; // 設置為循環播放
        source.connect(audioContext.destination);
        source.start(0);
    })
    .catch(error => console.error('Error loading audio:', error));
```

## 解釋
在使用 `AudioBufferSourceNode` 時，開發者應注意以下幾點：
- 每個 `AudioBufferSourceNode` 只能播放一次，若需重複播放，需重新創建新的源節點。
- 確保音頻上下文處於活動狀態，否則可能無法播放音頻（例如，當用戶未與頁面互動時，某些瀏覽器會暫停音頻上下文）。
- 在使用 `fetch` 加載音頻時，務必處理異常情況，避免未能加載音頻的問題。

## 總結
`AudioBufferSourceNode` 是 Web Audio API 中用於播放音頻數據的關鍵組件，簡化了音頻處理和播放的過程。