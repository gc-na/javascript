<!--
Meta Description: # DelayNode：在 JavaScript 中的延遲音訊節點 ## Synopsis DelayNode 是 Web Audio API 中的一種音訊節點，主要用於創建音訊延遲效果。它能夠在音訊信號傳輸過程中增加延遲時間，從而實現各種音效處理。 ## Documentation ### 目的 ...
Meta Keywords: delaynode, audiocontext, const, window, javascript
-->

# DelayNode：在 JavaScript 中的延遲音訊節點

## Synopsis
DelayNode 是 Web Audio API 中的一種音訊節點，主要用於創建音訊延遲效果。它能夠在音訊信號傳輸過程中增加延遲時間，從而實現各種音效處理。

## Documentation
### 目的
DelayNode 旨在處理和修改音訊信號，通過增加延遲來創造回聲或其他音效效果。這對於音樂製作和音訊效果的創建至關重要。

### 使用方法
要使用 DelayNode，首先需要創建一個音訊上下文（AudioContext），然後可以通過 `createDelay` 方法來創建 DelayNode 實例。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const delayNode = audioContext.createDelay();

// 設定延遲時間
delayNode.delayTime.value = 0.5; // 以秒為單位
```

### 詳細信息
- **屬性**：
  - `delayTime`：這是一個 `AudioParam`，用於設置延遲的時間。可以動態調整其值。
  
- **方法**：
  - `connect(destination)`：可以將 DelayNode 連接到其他音訊節點或音訊輸出。
  - `disconnect(destination)`：用於斷開與其他節點的連接。

使用 DelayNode 時，請確保在正確的音訊上下文中進行操作，且在播放音訊之前連接所有音訊節點。

## Examples
### 基本使用示例
以下是一個簡單的範例，展示如何使用 DelayNode 在音訊中添加延遲效果：

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = audioContext.createOscillator();
const delayNode = audioContext.createDelay();

// 設定延遲時間
delayNode.delayTime.value = 0.3; // 300 毫秒

// 連接音訊節點
oscillator.connect(delayNode);
delayNode.connect(audioContext.destination);

// 啟動振盪器
oscillator.start();
```

## Explanation
在使用 DelayNode 時，開發者需要注意以下常見問題：
- **延遲時間的範圍**：DelayNode 的延遲時間通常需要設置在合理的範圍內，過短或過長的延遲可能導致音訊效果不佳。
- **連接問題**：確保 DelayNode 正確連接到音訊上下文的目標上，以避免音訊無法播放。
- **性能考量**：使用過多的 DelayNode 可能影響性能，特別是在移動設備上。

## One Line Summary
DelayNode 是 Web Audio API 中用於在音訊信號中添加延遲效果的音訊節點。