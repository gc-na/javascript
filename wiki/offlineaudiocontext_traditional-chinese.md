<!--
Meta Description: # OfflineAudioContext: JavaScript 的線上音頻處理解決方案 ## 簡介 `OfflineAudioContext` 是一個 Web Audio API 的接口，允許開發者在不需要即時播放音頻的情況下，進行音頻處理和合成，並將處理後的音頻輸出為音頻緩衝區。這對於需要在背...
Meta Keywords: offlineaudiocontext, offlinecontext, samplerate, const, length
-->

# OfflineAudioContext: JavaScript 的線上音頻處理解決方案

## 簡介
`OfflineAudioContext` 是一個 Web Audio API 的接口，允許開發者在不需要即時播放音頻的情況下，進行音頻處理和合成，並將處理後的音頻輸出為音頻緩衝區。這對於需要在背景進行音頻處理的應用程序特別有用，如音頻效果的預渲染或音頻數據的生成。

## 文檔
`OfflineAudioContext` 的主要目的是提供一個可以在不播放聲音的情況下進行音頻處理的環境。這個接口可以用於創建一個離線音頻上下文，然後在這個上下文中進行音頻操作。

### 用法
要使用 `OfflineAudioContext`，您需要創建一個新的 `OfflineAudioContext` 實例。構造函數接受三個參數：

1. `numberOfChannels`: 音頻通道的數量（例如：1 表示單聲道，2 表示立體聲）。
2. `length`: 緩衝區的長度，以樣本為單位。
3. `sampleRate`: 音頻的採樣率（例如：44100 Hz）。

```javascript
const offlineContext = new OfflineAudioContext(numberOfChannels, length, sampleRate);
```

一旦創建了 `OfflineAudioContext`，您可以像使用 `AudioContext` 一樣操作它，並使用 `startRendering()` 方法來開始音頻處理。這個方法會返回一個 Promise，當音頻處理完成時，您可以獲取處理後的音頻緩衝區。

### 詳細步驟
1. 創建 `OfflineAudioContext` 實例。
2. 在上下文中添加音頻源和效果。
3. 調用 `startRendering()` 開始處理。
4. 使用返回的音頻緩衝區。

## 範例
以下是一個基本的示例，展示如何使用 `OfflineAudioContext` 來合成一個簡單的正弦波聲音。

```javascript
const sampleRate = 44100;
const length = sampleRate * 2; // 2 seconds
const offlineContext = new OfflineAudioContext(1, length, sampleRate);

const oscillator = offlineContext.createOscillator();
oscillator.frequency.setValueAtTime(440, offlineContext.currentTime); // A4
oscillator.connect(offlineContext.destination);
oscillator.start();

offlineContext.startRendering().then((renderedBuffer) => {
    // 音頻處理完成，可以使用 renderedBuffer
    console.log(renderedBuffer);
});
```

## 解釋
在使用 `OfflineAudioContext` 時，有一些常見的陷阱需要注意：

- **音頻延遲**: 雖然您可以在後台處理音頻，但這個過程可能需要一些時間，特別是對於複雜的音頻效果，因此請確保您的應用可以處理這種延遲。
- **記憶體使用**: 大型音頻緩衝區可能會佔用大量的記憶體，特別是在高採樣率和多通道時，請適當選擇參數以避免性能問題。
- **效果鏈**: 確保正確連接音頻節點，否則可能不會產生預期的音頻效果。

## 一句總結
`OfflineAudioContext` 允許開發者在不播放聲音的情況下進行音頻處理，並將結果輸出為音頻緩衝區，適合用於音頻效果預渲染和數據生成。