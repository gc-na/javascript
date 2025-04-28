<!--
Meta Description: # onended 事件在 JavaScript 中的應用 ## 概述 `onended` 事件是 Web Audio API 中的一個重要事件，用於監聽音頻播放結束的情況。當音頻的播放結束時，該事件會被觸發，開發者可以藉此進行後續操作，如釋放資源或播放下一段音頻。 ## 文檔 ### 目的 `on...
Meta Keywords: onended, audio, audioelement, const, audiocontext
-->

# onended 事件在 JavaScript 中的應用

## 概述
`onended` 事件是 Web Audio API 中的一個重要事件，用於監聽音頻播放結束的情況。當音頻的播放結束時，該事件會被觸發，開發者可以藉此進行後續操作，如釋放資源或播放下一段音頻。

## 文檔
### 目的
`onended` 事件的主要目的是提供一個回調機制，讓開發者能夠在音頻播放完成後執行特定的代碼。這對於多媒體應用程序來說非常重要，因為它可以幫助管理音頻的生命周期。

### 使用
`onended` 是一個事件處理器，通常用於 `Audio` 或 `AudioBufferSourceNode` 對象。當音頻播放完成時，開發者可以設置該事件的回調函數。

### 詳細說明
1. **設置事件處理器**：在創建音頻對象後，開發者需要指定 `onended` 屬性為一個函數。
2. **觸發事件**：當音頻播放結束時，該函數會被自動調用。
3. **事件對象**：事件本身不攜帶任何參數，但可以使用 `this` 關鍵字來獲取音頻對象。

## 範例
### 基本用法
以下是一個簡單的範例，展示如何使用 `onended` 事件：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const audioElement = new Audio('path/to/audio/file.mp3');
const track = audioContext.createMediaElementSource(audioElement);

// 設置 `onended` 事件
audioElement.onended = function() {
    console.log('音頻播放已結束。');
};

// 開始播放音頻
audioElement.play();
```

## 解釋
### 常見問題
1. **未觸發事件**：如果音頻因為錯誤或用戶干預（如暫停或停止）而未正常結束，`onended` 事件將不會被觸發。
2. **多次播放**：如果音頻需要重複播放，必須在每次播放前重新設置 `onended` 事件處理器。
3. **內存管理**：在音頻播放結束後，最好釋放不再需要的資源，以避免內存泄漏。

## 一句總結
`onended` 事件是 Web Audio API 中用於監聽音頻播放結束的重要事件，能幫助開發者進行後續操作。