<!--
Meta Description: # StereoPannerNode：JavaScript 中的立體聲平移節點 ## 簡介 StereoPannerNode 是 Web Audio API 中的一個節點，用於控制音頻信號的立體聲平移。它允許開發者將音頻信號在左聲道和右聲道之間進行平滑調整，創造出三維聲音效果。 ## 文件說明 St...
Meta Keywords: stereopannernode, audiocontext, panner, source, javascript
-->

# StereoPannerNode：JavaScript 中的立體聲平移節點

## 簡介
StereoPannerNode 是 Web Audio API 中的一個節點，用於控制音頻信號的立體聲平移。它允許開發者將音頻信號在左聲道和右聲道之間進行平滑調整，創造出三維聲音效果。

## 文件說明
StereoPannerNode 的主要用途是為了讓開發者能夠在立體聲場中定位音頻。這個節點可以接收音頻信號，並根據指定的平移值調整其聲音輸出，從而達到不同的聽覺效果。

### 使用方法
要使用 StereoPannerNode，首先需創建一個 AudioContext 實例，然後調用 `createStereoPanner()` 方法來生成此節點。其主要屬性包括：
- `pan`：取值範圍從 -1（全左）到 1（全右），0 則是中央。
- `connect()`：用於將節點連接到其他音頻節點或輸出裝置。

### 節點屬性
- **pan**：控制聲音的平移位置。
- **context**：返回與該節點相關聯的音頻上下文。

## 範例
以下是使用 StereoPannerNode 的基本範例：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建立體聲平移節點
const panner = audioContext.createStereoPanner();

// 設定平移值
panner.pan.value = -0.5; // 將聲音偏向左側

// 創建音源
const source = audioContext.createBufferSource();
// 加載音頻數據（假設已加載到 buffer 變數中）
source.buffer = buffer;

// 連接節點
source.connect(panner);
panner.connect(audioContext.destination);

// 播放音源
source.start();
```

## 解釋
使用 StereoPannerNode 時，開發者可能會遇到以下幾個常見問題：
1. **音量問題**：在調整平移值時，音量可能會變得不均勻，需注意平移的影響。
2. **連接順序**：確保音源正確連接到 StereoPannerNode，然後再連接到音頻上下文的輸出。
3. **瀏覽器相容性**：不同瀏覽器對 Web Audio API 的支持程度可能有所不同，測試時需注意。

## 一句總結
StereoPannerNode 使開發者能夠在 JavaScript 中靈活地控制音頻信號的立體聲平移，創造豐富的音效體驗。