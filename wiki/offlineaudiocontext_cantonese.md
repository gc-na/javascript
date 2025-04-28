<!--
Meta Description: # OfflineAudioContext：JavaScript 的離線音頻上下文 ## 概述 `OfflineAudioContext` 是一個 Web Audio API 的組件，允許開發者在不播放音頻的情況下進行音頻處理和合成。這對於音頻效果的預渲染或離線音頻分析特別有用。 ## 文件說明 `...
Meta Keywords: offlineaudiocontext, offlinecontext, 44100, javascript, const
-->

# OfflineAudioContext：JavaScript 的離線音頻上下文

## 概述
`OfflineAudioContext` 是一個 Web Audio API 的組件，允許開發者在不播放音頻的情況下進行音頻處理和合成。這對於音頻效果的預渲染或離線音頻分析特別有用。

## 文件說明
`OfflineAudioContext` 的目的是允許開發者在背景中處理音頻數據，然後將結果導出到音頻文件或其他用途。它提供了一個不需要播放音頻的上下文，讓開發者可以在指定的時間範圍內生成音頻數據。

### 用法
要創建一個 `OfflineAudioContext` 實例，你需要指定所需的聲道數、採樣率和持續時間（以秒為單位）：

```javascript
const offlineContext = new OfflineAudioContext(numberOfChannels, length, sampleRate);
```

- **numberOfChannels**：指定音頻通道的數量（例如：1 代表單聲道，2 代表立體聲）。
- **length**：指定音頻的總長度（以樣本數為單位）。
- **sampleRate**：指定音頻的採樣率（例如：44100 Hz）。

### 實例
以下是使用 `OfflineAudioContext` 的基本示例：

```javascript
// 創建一個 OfflineAudioContext
const offlineContext = new OfflineAudioContext(2, 44100 * 40, 44100);

// 創建一個音頻源
const audioBufferSource = offlineContext.createBufferSource();
const buffer = offlineContext.createBuffer(2, 44100 * 40, 44100); // 40秒的音頻

// 將音頻數據設置到音頻源中
audioBufferSource.buffer = buffer;

// 連接音頻源到上下文的目的地
audioBufferSource.connect(offlineContext.destination);

// 開始播放音頻源
audioBufferSource.start();

// 渲染音頻
offlineContext.startRendering().then(renderedBuffer => {
    console.log('音頻渲染完成', renderedBuffer);
});
```

## 解釋
使用 `OfflineAudioContext` 時，有一些常見的注意事項：

1. **限制**：在某些瀏覽器中，`OfflineAudioContext` 的最大持續時間可能受到限制。超過這個限制可能會導致錯誤。
   
2. **音頻效果**：在使用音頻效果（如濾波器或增益）時，請確保這些效果已正確連接到音頻源和目的地，否則渲染的音頻可能會有所不同。

3. **性能考量**：雖然 `OfflineAudioContext` 是為了處理音頻而設計，但處理大量音頻數據仍然可能會影響性能，因此應謹慎使用。

4. **異步行為**：`startRendering` 是一個異步方法，需使用 Promise 處理渲染結果。

## 一句總結
`OfflineAudioContext` 是一個強大的工具，允許開發者在 JavaScript 中進行高效的音頻處理而無需播放音頻。