<!--
Meta Description: # WaveShaperNode：JavaScript 音頻處理的關鍵工具 ## 摘要 WaveShaperNode 是 Web Audio API 中一個重要的音頻處理節點，允許開發者創建非線性響應的音頻效果，以達到失真和音色改變的效果。 ## 文檔 ### 目的 WaveShaperNode 主...
Meta Keywords: curve, waveshapernode, audiocontext, length, const
-->

# WaveShaperNode：JavaScript 音頻處理的關鍵工具

## 摘要
WaveShaperNode 是 Web Audio API 中一個重要的音頻處理節點，允許開發者創建非線性響應的音頻效果，以達到失真和音色改變的效果。

## 文檔
### 目的
WaveShaperNode 主要用於音頻信號的變形和失真處理。透過自定義的波形函數，它可以改變輸入信號的形狀，從而創造出獨特的音效。

### 使用方法
要使用 WaveShaperNode，首先需要創建一個 AudioContext，然後實例化 WaveShaperNode。接著，可以設置其 `curve` 屬性以定義波形，並將其連接到音頻圖中的其他節點。

#### 範例代碼：
```javascript
// 創建 AudioContext
const audioContext = new AudioContext();

// 創建 WaveShaperNode
const waveShaper = audioContext.createWaveShaper();

// 設置波形曲線
const curve = new Float32Array(2048);
for (let i = 0; i < curve.length; ++i) {
    curve[i] = (i < curve.length / 2) ? (i / (curve.length / 2)) : ((curve.length - i) / (curve.length / 2));
}
waveShaper.curve = curve;

// 創建音源並連接到 WaveShaperNode
const oscillator = audioContext.createOscillator();
oscillator.connect(waveShaper);
waveShaper.connect(audioContext.destination);

// 開始播放
oscillator.start();
```

## 解釋
使用 WaveShaperNode 時，開發者需要注意以下幾點：
1. **曲線設置**：`curve` 屬性必須是一個 Float32Array，數組的長度應為 2 的冪次方，並且值的範圍應在 -1 到 1 之間。
2. **音頻延遲**：WaveShaperNode 會引入延遲，因此在音頻處理鏈中應謹慎放置。
3. **性能問題**：過於複雜的曲線可能會影響性能，建議保持波形曲線的簡單性。

## 一句總結
WaveShaperNode 是一個強大的工具，可以用於創建獨特的音頻效果，特別是失真和音色變化。