<!--
Meta Description: # BaseAudioContext：JavaScript 音頻上下文的基礎 ## 概要 BaseAudioContext 是 Web Audio API 的核心組件，它提供了一個音頻處理的上下文，允許開發者創建和操作音頻圖形。 ## 文檔 BaseAudioContext 是所有音頻上下文的基類，...
Meta Keywords: baseaudiocontext, audiocontext, audioctx, javascript, web
-->

# BaseAudioContext：JavaScript 音頻上下文的基礎

## 概要
BaseAudioContext 是 Web Audio API 的核心組件，它提供了一個音頻處理的上下文，允許開發者創建和操作音頻圖形。

## 文檔
BaseAudioContext 是所有音頻上下文的基類，主要用於管理音頻的生成和處理。它的主要用途是建立音頻環境，讓開發者能夠進行音頻合成、音效處理以及音頻的播放控制。

### 主要屬性
- **sampleRate**: 返回上下文的取樣頻率，以赫茲為單位。
- **state**: 返回上下文的當前狀態，可能的值包括 "suspended"、"running" 和 "closed"。

### 主要方法
- **suspend()**: 暫停上下文的音頻處理。
- **resume()**: 恢復上下文的音頻處理。
- **close()**: 關閉上下文並釋放資源。

### 使用方式
要使用 BaseAudioContext，開發者通常會使用其子類，如 AudioContext 或 OfflineAudioContext 來創建音頻上下文。

## 示例
以下是使用 AudioContext 創建 BaseAudioContext 的基本範例：

```javascript
// 創建一個新的 AudioContext
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

// 檢查上下文的狀態
console.log(audioCtx.state); // 輸出 'suspended'

// 恢復音頻處理
audioCtx.resume().then(() => {
    console.log('AudioContext 已恢復');
});
```

## 解釋
在使用 BaseAudioContext 時，開發者應注意以下幾點：
- 在網頁加載時，瀏覽器通常會自動暫停音頻上下文，直到用戶與頁面互動。
- 確保在恢復或關閉上下文時，正確處理 Promise，以避免未處理的異常。
- 一旦上下文被關閉，再次使用該上下文將會導致錯誤，必須創建新的上下文實例。

## 一句總結
BaseAudioContext 是 Web Audio API 的基礎，用於音頻處理和控制的上下文管理。