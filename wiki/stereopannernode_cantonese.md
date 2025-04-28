<!--
Meta Description: # StereoPannerNode：JavaScript 音頻處理中的立體聲平衡器 ## 簡介 StereoPannerNode 是 Web Audio API 中的一個重要組件，允許開發者在立體聲聲道中平衡音頻信號，實現更具沉浸感的音效體驗。 ## 文檔 ### 目的 StereoPannerN...
Meta Keywords: stereopannernode, audiocontext, pan, panner, source
-->

# StereoPannerNode：JavaScript 音頻處理中的立體聲平衡器

## 簡介
StereoPannerNode 是 Web Audio API 中的一個重要組件，允許開發者在立體聲聲道中平衡音頻信號，實現更具沉浸感的音效體驗。

## 文檔
### 目的
StereoPannerNode 的目的是幫助開發者精確控制音頻的左右聲道平衡。它可以用於創建立體聲效果，讓用戶能夠感受到聲音的來源方向。

### 使用方法
要使用 StereoPannerNode，首先需要創建一個 AudioContext，然後實例化 StereoPannerNode。以下是基本的步驟：

1. 創建 AudioContext。
2. 創建 StereoPannerNode 實例。
3. 設定其 pan 屬性以控制聲音的左右位置。
4. 將音頻節點連接到音頻上下文的輸出。

### 詳細信息
- **屬性**：
  - `pan`: 一個介於 -1 和 1 之間的值，-1 代表全左，0 代表中間，1 代表全右。
- **方法**：
  - `connect()`: 將節點連接到其他音頻節點。
  - `disconnect()`: 斷開節點與其他音頻節點的連接。

## 範例
以下是一個基本的使用示例：

```javascript
// 創建一個音頻上下文
const audioContext = new AudioContext();

// 創建一個立體聲平衡器節點
const panner = audioContext.createStereoPanner();

// 設定 pan 屬性
panner.pan.value = -1; // 全左

// 創建一個音頻源
const source = audioContext.createBufferSource();
source.buffer = /* 這裡放置音頻緩衝區 */;

// 連接音頻源到平衡器
source.connect(panner);

// 連接平衡器到音頻上下文的輸出
panner.connect(audioContext.destination);

// 播放音頻
source.start();
```

## 解釋
在使用 StereoPannerNode 時，開發者需要注意以下幾點：
- **值的範圍**：確保 pan 屬性值在 -1 和 1 之間，超出範圍將導致不預期的行為。
- **音頻上下文的狀態**：在創建節點前，請確保音頻上下文處於運行狀態；如果上下文已暫停，則節點可能無法正常工作。
- **性能考量**：過多的音頻節點連接可能影響性能，建議優化音頻路徑。

## 總結
StereoPannerNode 是一個強大的工具，能幫助開發者在 JavaScript 中創建更具立體感的音頻效果，提升用戶的聽覺體驗。