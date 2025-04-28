<!--
Meta Description: # BiquadFilterNode：JavaScript 音頻處理中的濾波器節點 ## 簡介 BiquadFilterNode 是 Web Audio API 中的一個重要組件，用於音頻處理。它提供了一種方便的方式來應用不同類型的濾波器效果，例如低通、高通、帶通等，從而改變音頻信號的頻率響應。 #...
Meta Keywords: audiocontext, biquadfilter, biquadfilternode, source, const
-->

# BiquadFilterNode：JavaScript 音頻處理中的濾波器節點

## 簡介
BiquadFilterNode 是 Web Audio API 中的一個重要組件，用於音頻處理。它提供了一種方便的方式來應用不同類型的濾波器效果，例如低通、高通、帶通等，從而改變音頻信號的頻率響應。

## 文檔
### 目的
BiquadFilterNode 主要用於對音頻信號進行過濾處理，通過調整頻率響應來強化或減弱特定頻段的音頻。這在音樂制作和各種音頻應用中是非常重要的。

### 使用方法
要使用 BiquadFilterNode，首先需要創建一個 AudioContext，然後通過這個上下文創建 BiquadFilterNode 實例。以下是基本步驟：

1. 創建 AudioContext：
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. 創建 BiquadFilterNode：
   ```javascript
   const biquadFilter = audioContext.createBiquadFilter();
   ```

3. 設置濾波器類型和參數：
   ```javascript
   biquadFilter.type = 'lowpass'; // 可用類型：lowpass, highpass, bandpass, etc.
   biquadFilter.frequency.setValueAtTime(440, audioContext.currentTime);
   ```

4. 將濾波器連接到音頻源和音頻輸出：
   ```javascript
   const source = audioContext.createBufferSource();
   source.connect(biquadFilter);
   biquadFilter.connect(audioContext.destination);
   source.start();
   ```

### 詳細說明
BiquadFilterNode 提供了多種濾波器類型，通過 `type` 屬性來設置。常見的類型包括：
- `lowpass`：允許低頻信號通過，阻止高頻信號。
- `highpass`：允許高頻信號通過，阻止低頻信號。
- `bandpass`：僅允許特定頻段的信號通過。
- `notch`：阻止特定頻段的信號通過。

此外，BiquadFilterNode 還提供了一些屬性來控制濾波器的行為，例如 `frequency`、`Q` 和 `gain`。

## 示例
以下是使用 BiquadFilterNode 的簡單示例：

### 例子 1：低通濾波器
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const biquadFilter = audioContext.createBiquadFilter();
biquadFilter.type = 'lowpass';
biquadFilter.frequency.setValueAtTime(300, audioContext.currentTime);

const source = audioContext.createBufferSource();
// 假設 source.buffer 已經被設置為音頻數據
source.connect(biquadFilter);
biquadFilter.connect(audioContext.destination);
source.start();
```

### 例子 2：高通濾波器
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const biquadFilter = audioContext.createBiquadFilter();
biquadFilter.type = 'highpass';
biquadFilter.frequency.setValueAtTime(1500, audioContext.currentTime);

const source = audioContext.createBufferSource();
// 假設 source.buffer 已經被設置為音頻數據
source.connect(biquadFilter);
biquadFilter.connect(audioContext.destination);
source.start();
```

## 解釋
在使用 BiquadFilterNode 時，有幾個常見的陷阱需要注意：
- 確保音頻上下文已經正確啟動，否則音頻將無法播放。
- 濾波器參數（如頻率和增益）需要在合適的時間設置，以便在音頻播放時能夠正確生效。
- 當調整濾波器類型時，應考慮到音頻信號的特性，以避免不必要的失真或音質下降。

## 一句總結
BiquadFilterNode 是一個強大的工具，在 JavaScript 音頻處理中用於應用各種濾波效果，改變音頻信號的頻率響應。