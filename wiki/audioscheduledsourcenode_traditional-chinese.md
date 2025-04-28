<!--
Meta Description: # AudioScheduledSourceNode：JavaScript 中的音頻調度源節點 ## 概述 `AudioScheduledSourceNode` 是 Web Audio API 中的一個抽象類別，旨在提供一個基礎結構，用於創建和控制音頻源的調度，這些音頻源可以是音頻緩衝區、音頻播放或...
Meta Keywords: audiocontext, sourcenode, audioscheduledsourcenode, audio, const
-->

# AudioScheduledSourceNode：JavaScript 中的音頻調度源節點

## 概述
`AudioScheduledSourceNode` 是 Web Audio API 中的一個抽象類別，旨在提供一個基礎結構，用於創建和控制音頻源的調度，這些音頻源可以是音頻緩衝區、音頻播放或合成音頻的結果。透過這個節點，可以實現高效的音頻播放和精確的時間控制。

## 文件說明
`AudioScheduledSourceNode` 是 Web Audio API 的一部分，這個節點主要用於音頻信號的生成和調度。它的目的是使開發者能夠以高精度的方式播放音頻，並且可以指定音頻播放的起始和結束時間。這個節點通常不會直接實例化，而是由其他具體的音頻節點（如 `AudioBufferSourceNode` 和 `ConstantSourceNode`）繼承。

### 主要特性
- **時間控制**：可以精確控制音頻的播放時間。
- **事件處理**：提供對音頻播放狀態的事件監聽。
- **對其他節點的兼容性**：可以與其他音頻處理節點連接，以創建複雜的音頻處理流。

### 使用方法
使用 `AudioScheduledSourceNode` 的具體子類來創建音頻源，例如：

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const sourceNode = audioContext.createBufferSource(); // 這裡是具體的子類
sourceNode.buffer = audioBuffer; // 設定音頻緩衝區
sourceNode.connect(audioContext.destination); // 連接到音頻輸出
sourceNode.start(0); // 開始播放
```

## 範例
以下是使用 `AudioBufferSourceNode` 的基本範例：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 載入音頻文件
fetch('path/to/audio/file.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        const sourceNode = audioContext.createBufferSource();
        sourceNode.buffer = buffer; // 設定緩衝區
        sourceNode.connect(audioContext.destination); // 連接到輸出
        sourceNode.start(0); // 開始播放
    })
    .catch(error => console.error('Error with decoding audio data', error));
```

## 解釋
使用 `AudioScheduledSourceNode` 時，開發者需要注意以下幾點：

- **音頻上下文的狀態**：確保音頻上下文處於可播放狀態（如未被暫停），否則將無法播放音頻。
- **時間精度**：指定播放的開始和結束時間時，應該考慮到時間的精度，避免出現音頻播放不準確的情況。
- **資源管理**：使用完音頻節點後，應該釋放資源，例如通過 `stop()` 方法來停止播放，並釋放相關資源。

## 總結
`AudioScheduledSourceNode` 是 Web Audio API 中音頻調度的重要組件，通過它的子類可以實現高效的音頻播放和精確的時間控制。