<!--
Meta Description: # BaseAudioContext：JavaScript 音頻上下文的核心 ## 摘要 `BaseAudioContext` 是 Web Audio API 的一個基礎接口，負責處理音頻的生成和處理。它是所有音頻上下文的基礎，提供了音頻處理的基本功能。 ## 文檔 `BaseAudioContex...
Meta Keywords: baseaudiocontext, audiocontext, oscillator, javascript, web
-->

# BaseAudioContext：JavaScript 音頻上下文的核心

## 摘要
`BaseAudioContext` 是 Web Audio API 的一個基礎接口，負責處理音頻的生成和處理。它是所有音頻上下文的基礎，提供了音頻處理的基本功能。

## 文檔
`BaseAudioContext` 是 Web Audio API 的核心部分，所有的音頻上下文（如 `AudioContext` 和 `OfflineAudioContext`）都繼承自此接口。它允許開發者創建、編輯和播放音頻，並進行音效處理。

### 目的
`BaseAudioContext` 的目的是提供一個音頻處理環境，使開發者能夠使用 JavaScript 來控制音頻流。

### 使用
使用 `BaseAudioContext`，開發者能夠創建聲音源、連接音效處理節點並控制音頻播放。通常，開發者會使用 `AudioContext` 來實現這些功能，因為 `BaseAudioContext` 本身不允許直接實例化。

### 詳細信息
- **創建上下文**: 使用 `new AudioContext()` 創建一個新的音頻上下文。
- **音頻節點**: 可創建多種音頻節點（如 `GainNode`、`AnalyserNode` 等）來進行音頻處理。
- **播放音頻**: 使用 `AudioBufferSourceNode` 播放預加載的音頻。
- **音量控制**: 通過使用 `GainNode` 調整音量。
- **連接**: 使用 `connect()` 方法將不同的音頻節點連接在一起。

## 範例
以下是使用 `AudioContext`（繼承自 `BaseAudioContext`）的基本範例：

```javascript
// 創建音頻上下文
const audioContext = new AudioContext();

// 創建音頻源
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // 正弦波
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 設定頻率為 440Hz

// 連接音頻源到上下文的輸出
oscillator.connect(audioContext.destination);

// 開始播放
oscillator.start();
```

## 解釋
在使用 `BaseAudioContext` 和其派生類別時，開發者需注意以下幾點：
- **跨瀏覽器兼容性**: 在某些舊版本的瀏覽器中，Web Audio API 的支持可能有限。建議檢查瀏覽器的支持情況。
- **異步操作**: 音頻上下文的某些操作（如解碼音頻）是異步的，開發者需要妥善處理 Promise。
- **用戶交互要求**: 在許多瀏覽器中，音頻播放必須在用戶的交互下啟動，如點擊按鈕。

## 一句話總結
`BaseAudioContext` 是 JavaScript 中 Web Audio API 的基礎接口，為音頻處理提供了強大的功能。