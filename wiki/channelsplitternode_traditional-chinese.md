<!--
Meta Description: # ChannelSplitterNode：JavaScript 音訊處理的關鍵節點 ## 概述 `ChannelSplitterNode` 是 Web Audio API 中的一個重要組件，旨在將音訊流分割成多個獨立的聲道，以便進行更靈活的音訊處理。它特別適合於多聲道音訊的應用，如立體聲或多聲道音...
Meta Keywords: channelsplitternode, audiocontext, const, connect, splitter
-->

# ChannelSplitterNode：JavaScript 音訊處理的關鍵節點

## 概述
`ChannelSplitterNode` 是 Web Audio API 中的一個重要組件，旨在將音訊流分割成多個獨立的聲道，以便進行更靈活的音訊處理。它特別適合於多聲道音訊的應用，如立體聲或多聲道音樂播放。

## 文檔

### 目的
`ChannelSplitterNode` 的主要功能是將一個音訊信號分割成若干個獨立的音訊通道。這意味著您可以將音訊的不同部分分配到不同的處理路徑，從而實現更高效的音訊操作。

### 使用方法
要使用 `ChannelSplitterNode`，您首先需要創建一個 `AudioContext` 實例，然後使用該實例來創建 `ChannelSplitterNode`。以下是基本的使用步驟：

1. 創建 `AudioContext`。
2. 創建 `ChannelSplitterNode`。
3. 將音訊源連接到 `ChannelSplitterNode`。
4. 將分割的通道連接到其他音訊處理節點或輸出。

### 詳細信息
- **構造函數**：`ChannelSplitterNode` 的構造函數接受一個可選的參數 `numberOfOutputs`，默認值為 6，表示最多可分割成 6 個通道。
- **輸出**：每個輸出通道都是一個 `AudioNode`，您可以將它們連接到其他音訊處理節點，如增益、濾波器等。
- **應用場景**：適合用於音效設計、音樂製作、遊戲音訊等領域，特別在需要對多聲道音訊進行獨立處理的情況下。

## 範例

### 基本使用範例
以下是一個簡單的範例，展示如何創建 `ChannelSplitterNode` 並將其用於音訊處理：

```javascript
// 創建一個 AudioContext
const audioContext = new AudioContext();

// 創建一個 ChannelSplitterNode
const splitter = audioContext.createChannelSplitter(2); // 分割為兩個通道

// 創建音訊源（例如：使用 OscillatorNode）
const oscillator = audioContext.createOscillator();
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 音符
oscillator.start();

// 將音訊源連接到 ChannelSplitterNode
oscillator.connect(splitter);

// 將分割的通道連接到輸出
const gainNode1 = audioContext.createGain();
const gainNode2 = audioContext.createGain();

splitter.connect(gainNode1, 0); // 第一聲道
splitter.connect(gainNode2, 1); // 第二聲道

// 開始播放
gainNode1.connect(audioContext.destination);
gainNode2.connect(audioContext.destination);
```

## 解釋

### 常見陷阱
- **輸出數量限制**：注意，`ChannelSplitterNode` 的最大輸出數量是 32。如果您嘗試分割超過這個數量，將會引發錯誤。
- **音訊延遲**：在某些情況下，使用 `ChannelSplitterNode` 可能會導致音訊延遲，特別是在多次連接和處理節點時。

### 附加注意事項
- 在創建音訊上下文時，確認環境支持 Web Audio API。
- 確保所有連接都正確，以避免出現未預期的音訊行為。

## 一句話總結
`ChannelSplitterNode` 是 Web Audio API 中的音訊處理節點，用於將音訊流分割成多個獨立通道。