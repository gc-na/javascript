<!--
Meta Description: # ChannelSplitterNode：JavaScript 音頻處理中的分頻器節點 ## Synopsis ChannelSplitterNode 是 Web Audio API 中的一個重要組件，主要用於將單一音訊通道的輸入分割成多個音訊通道輸出，方便進行多通道音訊處理。 ## Docume...
Meta Keywords: audiocontext, channelsplitternode, const, splitter, javascript
-->

# ChannelSplitterNode：JavaScript 音頻處理中的分頻器節點

## Synopsis
ChannelSplitterNode 是 Web Audio API 中的一個重要組件，主要用於將單一音訊通道的輸入分割成多個音訊通道輸出，方便進行多通道音訊處理。

## Documentation
ChannelSplitterNode 是一種音訊處理節點，讓開發者能夠將一個音訊流按照通道數量進行分拆。它可以在音訊處理流程中創建多個輸出，每個輸出都代表了原始音訊流中的一個通道。這對於需要獨立處理每個通道的應用場景，例如立體聲音訊的左右聲道分離，特別有用。

### 目的
- 將音訊分開，便於獨立處理和效果應用。
- 提供更靈活的音訊處理能力，支持多通道音訊的操作。

### 使用方法
要創建一個 ChannelSplitterNode，首先需要一個 AudioContext 實例。接著，可以調用 `createChannelSplitter()` 方法來產生節點。

#### 語法
```javascript
const splitter = audioContext.createChannelSplitter(numberOfOutputs);
```

#### 參數
- `numberOfOutputs`：一個整數，指定要生成的輸出通道數量。這個數字必須在 1 到 32 之間。

### 範例
以下是一個簡單的示例，演示如何使用 ChannelSplitterNode 將一個立體聲音訊流分割為兩個獨立的通道。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const splitter = audioContext.createChannelSplitter(2);

// 假設我們有一個音訊源
const source = audioContext.createBufferSource();
// 將音訊源連接到分頻器
source.connect(splitter);

// 將分頻器的輸出連接到不同的效果器或輸出
const leftChannel = splitter.connect(audioContext.destination, 0); // 左聲道
const rightChannel = splitter.connect(audioContext.destination, 1); // 右聲道

// 開始播放音訊
source.start();
```

### 解釋
在使用 ChannelSplitterNode 時，有一些常見的陷阱和注意事項：

1. **通道數量限制**：`numberOfOutputs` 參數必須在 1 到 32 之間，超過這個範圍將會導致錯誤。
2. **連接順序**：確保在將音訊源連接到分頻器之後，再將分頻器的輸出連接到目的地或其他音訊處理節點。
3. **不支持的設備**：某些舊版瀏覽器可能不完全支持 Web Audio API，確保進行相容性測試。

## One Line Summary
ChannelSplitterNode 是一種 Web Audio API 組件，用來將單一音訊通道輸入分割為多個音訊通道輸出，方便獨立處理音訊。