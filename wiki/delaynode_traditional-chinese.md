<!--
Meta Description: # DelayNode：JavaScript 中的音頻處理延遲節點 ## 概述 DelayNode 是 Web Audio API 中一個重要的音頻處理節點，允許開發者在音頻信號上應用延遲效果。這對於創建回聲、延遲效果或其他音頻處理應用程序非常有用。 ## 文檔 ### 目的 DelayNode 的...
Meta Keywords: delaynode, audiocontext, oscillator, delaytime, connect
-->

# DelayNode：JavaScript 中的音頻處理延遲節點

## 概述
DelayNode 是 Web Audio API 中一個重要的音頻處理節點，允許開發者在音頻信號上應用延遲效果。這對於創建回聲、延遲效果或其他音頻處理應用程序非常有用。

## 文檔
### 目的
DelayNode 的主要目的是在音頻信號中引入延遲，使得音頻訊號在播放時可以有時間上的間隔。這對於音樂製作、遊戲音效及其他需要音頻處理的應用至關重要。

### 使用
DelayNode 的使用需要先創建一個 AudioContext，然後再使用該上下文創建 DelayNode。開發者可以設置延遲時間和反射時間，以精確控制音頻效果。

#### 創建 DelayNode 的基本步驟：
1. 創建 AudioContext。
2. 使用 `createDelay()` 方法創建 DelayNode。
3. 設定延遲時間。
4. 將 DelayNode 連接到音頻源和目標輸出。

### 詳細說明
DelayNode 具有以下主要屬性：
- **delayTime**：一個 AudioParam，表示音頻信號的延遲時間，單位為秒。可以通過設置這個屬性來調整延遲效果的持續時間。

DelayNode 還有以下方法：
- **connect(destination)**：將 DelayNode 連接到其他音頻節點。
- **disconnect(destination)**：斷開與其他音頻節點的連接。

## 範例
以下是使用 DelayNode 的基本範例：

```javascript
// 創建一個 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 DelayNode
const delayNode = audioContext.createDelay();

// 設定延遲時間為 0.5 秒
delayNode.delayTime.value = 0.5;

// 創建音頻源
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);

// 將音頻源連接到 DelayNode
oscillator.connect(delayNode);

// 將 DelayNode 連接到音頻輸出
delayNode.connect(audioContext.destination);

// 開始播放音頻源
oscillator.start();
```

## 解釋
在使用 DelayNode 時，開發者需要注意以下幾點：
- **延遲時間的範圍**：delayTime 屬性可以接受的值範圍是從 0 到 60 秒，但在實際應用中，較長的延遲時間可能會導致音質下降。
- **連接的順序**：確保音頻源正確連接到 DelayNode，然後再連接到輸出，否則可能無法聽到預期的音效。
- **性能考量**：過多的音頻處理節點會影響性能，特別是在移動設備上，因此應注意節點的使用數量。

## 總結
DelayNode 是 Web Audio API 中強大的音頻處理工具，能夠為音頻信號添加延遲效果，提升音樂和遊戲音效的創造性。