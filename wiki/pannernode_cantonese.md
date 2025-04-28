<!--
Meta Description: # PannerNode：JavaScript 中的空間音效處理節點 ## 簡介 PannerNode 是 Web Audio API 中的一個重要組件，專門用來處理聲音的空間定位效果。它允許開發者在三維空間中精確地控制聲音的方向和距離，從而增強用戶的沉浸感。 ## 文檔 PannerNode 的主...
Meta Keywords: pannernode, audiocontext, javascript, source, const
-->

# PannerNode：JavaScript 中的空間音效處理節點

## 簡介
PannerNode 是 Web Audio API 中的一個重要組件，專門用來處理聲音的空間定位效果。它允許開發者在三維空間中精確地控制聲音的方向和距離，從而增強用戶的沉浸感。

## 文檔
PannerNode 的主要目的是為了創建三維聲音環境。它能夠模擬聲音源在空間中的移動，並根據聲源和聽者之間的相對位置來調整音量和聲音的音色。

### 使用方法
要使用 PannerNode，首先需要創建一個 AudioContext，然後使用 `createPanner()` 方法來實例化 PannerNode。以下是基本的步驟：

1. 創建 AudioContext：
   ```javascript
   const audioContext = new AudioContext();
   ```
   
2. 創建 PannerNode：
   ```javascript
   const pannerNode = audioContext.createPanner();
   ```

3. 設置 PannerNode 的屬性，例如：
   ```javascript
   pannerNode.panningModel = 'HRTF'; // 使用 HRTF 音頻模型
   pannerNode.setPosition(0, 0, 0);   // 設置聲源位置
   ```

4. 將聲音源連接到 PannerNode，再將 PannerNode 連接到 AudioContext 的輸出：
   ```javascript
   const source = audioContext.createBufferSource();
   source.buffer = audioBuffer; // 假設 audioBuffer 是加載的音頻數據
   source.connect(pannerNode);
   pannerNode.connect(audioContext.destination);
   ```

### 詳細說明
PannerNode 提供了多種屬性和方法來調整聲音效果，包括：

- `panningModel`: 設置使用的平移模型（如 HRTF 或 equalpower）。
- `distanceModel`: 控制距離衰減模型（如 linear、inverse、exponential）。
- `refDistance` 和 `maxDistance`: 設置聲音的參考距離和最大距離。
- `setPosition(x, y, z)`: 設置聲源在三維空間中的位置。

這些屬性可以幫助開發者根據需要調整聲音的空間感，從而創建更真實的聽覺體驗。

## 示例
以下是 PannerNode 的基本用法示例：

```javascript
const audioContext = new AudioContext();
const pannerNode = audioContext.createPanner();

pannerNode.panningModel = 'HRTF';
pannerNode.setPosition(5, 0, 0); // 將聲源放在 (5, 0, 0) 的位置

const source = audioContext.createBufferSource();
// 假設 audioBuffer 是已加載的音頻數據
source.buffer = audioBuffer;
source.connect(pannerNode);
pannerNode.connect(audioContext.destination);
source.start();
```

## 解釋
在使用 PannerNode 時，開發者可能會遇到以下常見問題：

- **音效不明顯**：確保聲源和聽者的相對位置正確，並檢查距離模型設置是否合適。
- **兼容性問題**：某些瀏覽器對於 Web Audio API 的支持程度不同，應當檢查最新的瀏覽器兼容性資料。
- **性能考量**：在大量使用 PannerNode 時，可能會影響性能，建議在需要時才創建新的實例。

## 一句話總結
PannerNode 是一個強大的工具，能夠在 JavaScript 中為聲音添加三維空間效果，提升用戶沉浸感。