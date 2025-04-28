<!--
Meta Description: # AudioBuffer：JavaScript 中的音訊緩衝區 ## 簡介 `AudioBuffer` 是 Web Audio API 中的一個重要組件，用於儲存和處理音訊數據。它提供了一個高效的方式來處理音訊樣本，使得開發者能夠進行高品質的音訊操作和播放。 ## 文檔 ### 目的 `Audio...
Meta Keywords: audiocontext, audiobuffer, buffer, const, javascript
-->

# AudioBuffer：JavaScript 中的音訊緩衝區

## 簡介
`AudioBuffer` 是 Web Audio API 中的一個重要組件，用於儲存和處理音訊數據。它提供了一個高效的方式來處理音訊樣本，使得開發者能夠進行高品質的音訊操作和播放。

## 文檔

### 目的
`AudioBuffer` 的主要目的是提供一個可以在內存中儲存音訊數據的緩衝區。這使得開發者可以進行各種音訊處理，例如編輯、播放和合成音訊。

### 使用方式
要創建一個 `AudioBuffer`，首先需要通過 `AudioContext` 物件來獲取音訊上下文。然後，可以使用 `createBuffer` 方法來創建一個新的音訊緩衝區。

```javascript
const audioContext = new AudioContext();
const buffer = audioContext.createBuffer(numberOfChannels, length, sampleRate);
```

- **numberOfChannels**：整數，表示音訊的通道數（如單聲道為 1，立體聲為 2）。
- **length**：整數，表示音訊緩衝區的長度，以樣本數為單位。
- **sampleRate**：數字，表示音訊的取樣率，以赫茲為單位（例如 44100 Hz）。

### 詳細信息
`AudioBuffer` 物件包含了多個方法和屬性，這些方法和屬性可用於讀取和寫入音訊數據。開發者可以使用 `getChannelData(channel)` 方法來獲取特定通道的音訊數據，並進行操作。

```javascript
const channelData = buffer.getChannelData(0); // 獲取第一通道的音訊數據
```

此外，`AudioBuffer` 還支持多種音訊格式和編碼，使其成為音訊處理的靈活選擇。

## 範例

以下是創建和使用 `AudioBuffer` 的基本範例：

```javascript
const audioContext = new AudioContext();
const buffer = audioContext.createBuffer(2, audioContext.sampleRate * 2, audioContext.sampleRate);

// 填充音訊數據
for (let channel = 0; channel < buffer.numberOfChannels; channel++) {
    const nowBuffering = buffer.getChannelData(channel);
    for (let i = 0; i < buffer.length; i++) {
        nowBuffering[i] = Math.random() * 2 - 1; // 填充隨機數據
    }
}

// 播放音訊
const source = audioContext.createBufferSource();
source.buffer = buffer;
source.connect(audioContext.destination);
source.start(0);
```

## 解釋

### 常見問題
- **音訊緩衝區大小限制**：在某些瀏覽器中，`AudioBuffer` 的大小可能受到限制，確保不要超過這些限制。
- **音訊延遲**：由於音訊處理的複雜性，可能會導致音訊播放時出現延遲，調整緩衝區大小可以幫助改善此問題。

### 附加注意事項
- `AudioBuffer` 是不可變的，創建後無法調整其大小。
- 確保在使用 `AudioBuffer` 之前，`AudioContext` 已經處於運行狀態。

## 一行總結
`AudioBuffer` 是 JavaScript 中用於儲存和處理音訊數據的強大工具，讓開發者能夠實現高效的音訊操作。