<!--
Meta Description: # IIRFilterNode：JavaScript 音效處理中的無限脈衝響應濾波器節點 ## 概述 IIRFilterNode 是 Web Audio API 中的一種濾波器節點，允許開發者使用無限脈衝響應（IIR）濾波器來處理音頻信號。它能夠實現複雜的音頻效果，並能夠高效地進行音頻信號的濾波處理...
Meta Keywords: iirfilternode, audiocontext, const, audio, web
-->

# IIRFilterNode：JavaScript 音效處理中的無限脈衝響應濾波器節點

## 概述
IIRFilterNode 是 Web Audio API 中的一種濾波器節點，允許開發者使用無限脈衝響應（IIR）濾波器來處理音頻信號。它能夠實現複雜的音頻效果，並能夠高效地進行音頻信號的濾波處理。

## 文檔
### 目的
IIRFilterNode 的主要目的在於提供一種高效的方式來實現各種音頻濾波器效果，例如低通濾波器、高通濾波器、帶通濾波器等。與其他類型的濾波器相比，IIR 濾波器能以較少的計算量達成較高的濾波效果。

### 使用方法
要使用 IIRFilterNode，你需要首先創建一個 AudioContext，然後使用 `createIIRFilter` 方法來實例化 IIRFilterNode。以下是基本的使用流程：

1. 創建 AudioContext。
2. 定義濾波係數。
3. 使用 `createIIRFilter` 方法創建 IIRFilterNode。
4. 將其連接到音頻信號流中。

### 詳細說明
IIRFilterNode 接受兩個參數：
- `feedforward`：一個數字數組，定義濾波器的前饋係數。
- `feedback`：一個數字數組，定義濾波器的反饋係數。

這些係數會影響音頻信號的濾波效果，正確的設置能夠實現期望的聲音效果。

## 範例
以下是一個簡單的範例，展示如何使用 IIRFilterNode 來創建一個低通濾波器：

```javascript
// 創建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 定義濾波器係數
const feedforward = [0.1, 0.1];  // 前饋係數
const feedback = [0.2, 0.2];      // 反饋係數

// 創建 IIRFilterNode
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);

// 創建音源（例如：音頻檔案）
const audioElement = new Audio('path/to/audio.mp3');
const sourceNode = audioContext.createMediaElementSource(audioElement);

// 將音源連接到 IIRFilterNode，然後連接到音頻輸出
sourceNode.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

// 播放音頻
audioElement.play();
```

## 解釋
在使用 IIRFilterNode 時，有幾個常見的陷阱需要避免：
- **係數設定不當**：不正確的濾波係數可能會導致不理想的聲音效果，甚至引入噪音。
- **音頻上下文的管理**：確保 AudioContext 在使用時保持活躍，否則將無法正確播放音頻。
- **跨瀏覽器兼容性**：某些瀏覽器可能對 Web Audio API 的支持有所不同，需進行兼容性測試。

## 一句話總結
IIRFilterNode 是 Web Audio API 中一種高效的濾波器節點，透過無限脈衝響應技術實現音頻信號的精確處理。