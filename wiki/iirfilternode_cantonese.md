<!--
Meta Description: # IIRFilterNode：JavaScript 中的 IIR 濾波器節點 ## 簡介 IIRFilterNode 是 Web Audio API 中的一個功能，用於實現無限脈衝響應濾波器。它能夠讓開發者對音頻信號進行高效的濾波處理，適合用於音頻效果和音頻分析。 ## 文件說明 IIRFilte...
Meta Keywords: iirfilternode, audiocontext, const, source, feedforward
-->

# IIRFilterNode：JavaScript 中的 IIR 濾波器節點

## 簡介
IIRFilterNode 是 Web Audio API 中的一個功能，用於實現無限脈衝響應濾波器。它能夠讓開發者對音頻信號進行高效的濾波處理，適合用於音頻效果和音頻分析。

## 文件說明
IIRFilterNode 的主要用途是對音頻信號進行濾波操作，透過指定的係數來實現無限脈衝響應（IIR）。這個節點適用於需要高性能音訊處理的應用，例如音樂製作軟件、即時音效處理等。

### 語法
```javascript
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);
```

### 參數
- **feedforward**: 一個數組，包含濾波器的前饋係數。
- **feedback**: 一個數組，包含濾波器的回饋係數。

### 返回值
返回一個 IIRFilterNode 實例，可以用於音頻處理鏈中。

## 使用範例
### 基本示例
以下是一個簡單的示例，展示如何創建一個 IIRFilterNode 並將其連接到音頻上下文中。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const iirFilterNode = audioContext.createIIRFilter([1, -1], [0.5, 0.5]);

const source = audioContext.createBufferSource();
// 假設 buffer 是一個有效的音頻緩衝區
source.buffer = buffer;

source.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);
source.start();
```

### 高級示例
以下示例展示如何使用不同的係數來調整濾波器的行為。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const feedforward = [1, -0.5];
const feedback = [0.5, 0.25];

const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);

const source = audioContext.createBufferSource();
source.buffer = buffer;

source.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);
source.start();
```

## 解釋
在使用 IIRFilterNode 時，有幾個常見的誤區和注意事項：

1. **濾波器係數的選擇**：不正確的係數可能會導致音質下降或不預期的結果。在設計濾波器時，需仔細選擇 feedforward 和 feedback 係數。

2. **性能考量**：IIR 濾波器通常比 FIR 濾波器在計算上更高效，但同時也可能更難以設計。開發者需根據實際需求選擇合適的濾波器類型。

3. **音頻上下文的管理**：確保在使用 IIRFilterNode 前，正確創建和管理音頻上下文，否則可能會導致錯誤或不正確的行為。

## 總結
IIRFilterNode 是一個強大的工具，用於實現高效的音頻濾波，適合需要即時音頻處理的應用。