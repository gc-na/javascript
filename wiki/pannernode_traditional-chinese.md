<!--
Meta Description: # PannerNode：JavaScript 中的三維音頻定位器 ## 摘要 PannerNode 是 Web Audio API 中的一個節點，用於創建三維音頻效果，允許開發者在三維空間中定位聲音源，提高音頻的沉浸感。 ## 文檔 PannerNode 是 Web Audio API 的一部分，...
Meta Keywords: pannernode, panner, audiocontext, const, web
-->

# PannerNode：JavaScript 中的三維音頻定位器

## 摘要
PannerNode 是 Web Audio API 中的一個節點，用於創建三維音頻效果，允許開發者在三維空間中定位聲音源，提高音頻的沉浸感。

## 文檔
PannerNode 是 Web Audio API 的一部分，其主要目的是在三維空間中控制音頻的定位和聲場效果。透過 PannerNode，開發者可以設置聲音源的方向、位置和音量衰減，從而創造出更加真實的音頻體驗。

### 使用方法
要使用 PannerNode，首先必須創建一個 AudioContext，然後再創建 PannerNode 實例。PannerNode 提供了多種屬性和方法來調整音頻定位和效果。

#### 基本屬性
- **panningModel**：設定聲音定位模型，選擇 `equalpower` 或 `HRTF`。
- **distanceModel**：選擇距離模型，選擇 `linear`、`inverse` 或 `exponential`。
- **refDistance**：參考距離，聲音從此距離開始衰減。
- **maxDistance**：最大距離，超過此距離後聲音不再衰減。
- **rolloffFactor**：衰減因子，影響聲音隨距離的衰減速度。

#### 使用範例
```javascript
// 創建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 PannerNode
const panner = audioContext.createPanner();

// 設定 PannerNode 屬性
panner.panningModel = 'HRTF';
panner.distanceModel = 'linear';
panner.refDistance = 1;
panner.maxDistance = 100;
panner.rolloffFactor = 1;

// 創建音頻源
const audioElement = new Audio('sound.mp3');
const track = audioContext.createMediaElementSource(audioElement);

// 連接音頻源到 PannerNode，然後連接到 AudioContext
track.connect(panner);
panner.connect(audioContext.destination);

// 設定聲音位置
panner.setPosition(0, 0, -5); // 在 z 軸上距離 -5 的位置

// 播放音樂
audioElement.play();
```

## 說明
在使用 PannerNode 時，開發者可能會遇到一些常見的問題：

1. **音量問題**：如果音頻聽起來過於微弱，檢查 PannerNode 的屬性設置，特別是 `refDistance` 和 `maxDistance`。
2. **方向性**：確保正確設置聲音源的方向，使用 `setOrientation` 方法來調整聽者的朝向。
3. **性能考量**：在移動 PannerNode 的位置時，頻繁更新可能會影響性能。建議在動畫循環中進行更新。

## 總結
PannerNode 是一個強大的工具，能夠為 Web 應用程序提供三維音頻定位效果，使開發者能夠創造出更具沉浸感的音頻體驗。透過合適的屬性和方法設置，PannerNode 可以有效地提升音頻的真實感和臨場感。