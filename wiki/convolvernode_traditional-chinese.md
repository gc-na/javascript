<!--
Meta Description: # ConvolverNode：JavaScript 中的音訊處理工具 ## 概述 ConvolverNode 是 Web Audio API 中的一個重要接口，用於實現卷積響應（Convolution Reverb），以創建逼真的聲音環境效果。這個節點可以將音頻信號與一個脈衝響應（Impulse ...
Meta Keywords: convolvernode, audiocontext, buffer, response, convolver
-->

# ConvolverNode：JavaScript 中的音訊處理工具

## 概述
ConvolverNode 是 Web Audio API 中的一個重要接口，用於實現卷積響應（Convolution Reverb），以創建逼真的聲音環境效果。這個節點可以將音頻信號與一個脈衝響應（Impulse Response，簡稱 IR）進行卷積，從而模擬不同空間的聲音特性。

## 文檔

### 目的
ConvolverNode 的主要目的是提供一種方法來模擬環境聲音的響應，讓開發者能夠為音頻應用添加自然的混響效果。這對於音樂製作、遊戲開發以及其他需要聲音真實感的應用特別有用。

### 使用方法
要使用 ConvolverNode，首先需要創建一個 AudioContext 實例，然後利用此上下文創建 ConvolverNode。接著，將所需的脈衝響應音頻加載到 ConvolverNode 中，最後將其連接到音頻信號的處理路徑中。

### 主要屬性和方法
- **buffer**: 設置或獲取 ConvolverNode 的脈衝響應音頻緩衝區。
- **normalize**: 設置是否正規化脈衝響應，以防止音量過高。

## 範例

### 基本用法
以下是如何創建一個 ConvolverNode 並將其應用於音頻信號的範例：

```javascript
// 創建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 ConvolverNode
const convolver = audioContext.createConvolver();

// 載入脈衝響應音頻
fetch('path/to/impulse-response.wav')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    convolver.buffer = buffer;
  })
  .catch(error => console.error(error));

// 創建音源
const source = audioContext.createBufferSource();
source.buffer = /* 你的音頻緩衝區 */;

// 將音源連接到 ConvolverNode
source.connect(convolver);

// 將 ConvolverNode 連接到音頻上下文的輸出
convolver.connect(audioContext.destination);

// 播放音源
source.start();
```

## 說明

### 常見問題與注意事項
- **脈衝響應文件的格式**：確保使用正確格式（如 WAV 或 AIFF）的脈衝響應文件，因為不支持的格式可能導致錯誤。
- **音量控制**：使用 ConvolverNode 可能導致音量增強，因此建議在使用前對輸出進行音量控制。
- **性能考量**：處理大型脈衝響應文件會增加 CPU 負擔，應根據需求選擇合適的文件大小。

## 一句總結
ConvolverNode 是 Web Audio API 中一個強大的工具，可用於創建真實的聲音環境效果，通過卷積響應技術提升音頻應用的沉浸感。