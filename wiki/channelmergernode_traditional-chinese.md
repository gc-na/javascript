<!--
Meta Description: # ChannelMergerNode：JavaScript 音頻處理中的關鍵節點 ## 簡介 ChannelMergerNode 是 Web Audio API 中的一個重要功能，允許開發者將多個音頻通道合併為一個音頻流。這對於音頻混合和多通道音頻處理尤為重要。 ## 文檔 ### 目的 Chan...
Meta Keywords: channelmergernode, audioctx, const, merger, window
-->

# ChannelMergerNode：JavaScript 音頻處理中的關鍵節點

## 簡介
ChannelMergerNode 是 Web Audio API 中的一個重要功能，允許開發者將多個音頻通道合併為一個音頻流。這對於音頻混合和多通道音頻處理尤為重要。

## 文檔
### 目的
ChannelMergerNode 的主要目的是將多個音頻輸入通道合併為一個單一的輸出信號。這使得開發者能夠在音樂、遊戲以及其他音頻應用中自由地操作和混合多個音頻源。

### 使用方法
要使用 ChannelMergerNode，首先需要創建一個 AudioContext 實例，然後使用 `createChannelMerger()` 方法來生成一個 ChannelMergerNode 實例。該方法可以接受一個可選的參數，指定合併的通道數量（默認為 6）。

```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const merger = audioCtx.createChannelMerger(2); // 產生一個合併兩個通道的節點
```

### 參數
- **numberOfChannels** (可選)：指定要合併的音頻通道數量，範圍從 1 到 32。

### 輸入和輸出
- **輸入**：ChannelMergerNode 支持多個音頻輸入，這些輸入可以來自不同的音頻源。
- **輸出**：合併後的音頻數據可以通過 `connect()` 方法連接到其他音頻節點，如音量控制、效果處理器或直接輸出到揚聲器。

## 範例
以下是一個簡單的示例，展示如何使用 ChannelMergerNode 合併兩個音頻通道：

```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const source1 = audioCtx.createBufferSource();
const source2 = audioCtx.createBufferSource();
const merger = audioCtx.createChannelMerger(2);

// 假設 source1 和 source2 已經被設置了音頻緩衝區
source1.connect(merger, 0, 0); // 將第一個音源連接到合併器的第一個通道
source2.connect(merger, 0, 1); // 將第二個音源連接到合併器的第二個通道

merger.connect(audioCtx.destination); // 將合併後的音頻輸出到揚聲器

source1.start(); // 開始播放音源
source2.start(); // 開始播放第二個音源
```

## 解釋
### 常見問題
1. **通道數量限制**：ChannelMergerNode 最多支持 32 個通道，超出這個數量將導致錯誤。
2. **音頻延遲**：合併多個音源可能會引入延遲，確保音頻節點按正確的順序連接以最小化延遲。
3. **兼容性**：確保使用的瀏覽器支持 Web Audio API，否則 ChannelMergerNode 將無法使用。

## 一句話總結
ChannelMergerNode 是 Web Audio API 的一個功能強大的節點，用於合併多個音頻通道，適用於音頻混合和處理。