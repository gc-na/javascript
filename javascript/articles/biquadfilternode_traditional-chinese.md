<!--
Meta Description: # BiquadFilterNode：JavaScript 音頻處理的強大工具 ## 概述 BiquadFilterNode 是 Web Audio API 中的一種音頻節點，用於對音頻信號進行濾波處理。它能夠創建多種濾波效果，並廣泛應用於音效設計和音頻處理。 ## 文檔 BiquadFilterN...
Meta Keywords: audiocontext, biquadfilter, biquadfilternode, javascript, const
-->

# BiquadFilterNode：JavaScript 音頻處理的強大工具

## 概述
BiquadFilterNode 是 Web Audio API 中的一種音頻節點，用於對音頻信號進行濾波處理。它能夠創建多種濾波效果，並廣泛應用於音效設計和音頻處理。

## 文檔
BiquadFilterNode 的主要目的是提供一個簡單的接口來應用二階濾波器於音頻信號上。這種濾波器能夠調整音頻的頻率響應，常見的濾波器類型包括低通、高通、帶通、帶阻和峰值濾波器。

### 使用方法
要使用 BiquadFilterNode，通常需要以下步驟：

1. **創建音頻上下文**：
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. **創建 BiquadFilterNode**：
   ```javascript
   const biquadFilter = audioContext.createBiquadFilter();
   ```

3. **設置濾波器類型與參數**：
   ```javascript
   biquadFilter.type = 'lowpass'; // 濾波器類型
   biquadFilter.frequency.setValueAtTime(440, audioContext.currentTime); // 頻率設置
   ```

4. **連接音頻源**：
   ```javascript
   const source = audioContext.createBufferSource(); // 創建音頻源
   source.connect(biquadFilter);
   biquadFilter.connect(audioContext.destination); // 連接到輸出
   ```

5. **播放音頻**：
   ```javascript
   source.start();
   ```

### 詳細說明
BiquadFilterNode 提供了多種濾波器類型，通過設置 `type` 屬性可以選擇：

- `lowpass`：僅允許低於指定頻率的信號通過。
- `highpass`：僅允許高於指定頻率的信號通過。
- `bandpass`：僅允許在特定頻率範圍內的信號通過。
- `lowshelf`：降低指定頻率以下的信號。
- `highshelf`：降低指定頻率以上的信號。
- `peaking`：在指定頻率範圍內提高或降低信號。

## 示例
以下是使用 BiquadFilterNode 的基本示例：

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const biquadFilter = audioContext.createBiquadFilter();

biquadFilter.type = 'lowpass';
biquadFilter.frequency.setValueAtTime(440, audioContext.currentTime);

const source = audioContext.createBufferSource(); // 假設已經加載音頻數據
source.connect(biquadFilter);
biquadFilter.connect(audioContext.destination);

source.start();
```

## 解釋
使用 BiquadFilterNode 時需注意以下幾點：

- 確保音頻上下文已經啟動：在某些瀏覽器中，音頻上下文必須在用戶互動後啟動。
- 濾波器類型必須正確設置，以確保所需的音效。
- 在連接音頻源和濾波器之前，必須先創建音頻源。

## 一句話總結
BiquadFilterNode 是一種靈活的音頻處理工具，能夠在 Web Audio API 中創建多種濾波效果。