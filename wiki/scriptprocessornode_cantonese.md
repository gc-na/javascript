<!--
Meta Description: # ScriptProcessorNode：JavaScript 中的音頻處理節點 ## 概述 `ScriptProcessorNode` 是 Web Audio API 中的一種音頻處理節點，允許開發者以 JavaScript 編寫自定義的音頻處理算法，實現實時音頻處理和操作。 ## 文檔 `Sc...
Meta Keywords: scriptprocessornode, const, javascript, audiocontext, channel
-->

# ScriptProcessorNode：JavaScript 中的音頻處理節點

## 概述
`ScriptProcessorNode` 是 Web Audio API 中的一種音頻處理節點，允許開發者以 JavaScript 編寫自定義的音頻處理算法，實現實時音頻處理和操作。

## 文檔
`ScriptProcessorNode` 主要用於音頻信號的實時處理，開發者可以創建音頻應用程式，進行音頻的生成、分析或效果處理。這個節點能夠提供一個音頻緩衝區，其中包含了音頻數據，並允許用戶編寫 JavaScript 函數來處理這些數據。

### 建立 `ScriptProcessorNode`
要創建一個 `ScriptProcessorNode`，你需要使用 `AudioContext` 對象的 `createScriptProcessor()` 方法。這個方法的參數包括：
- `bufferSize`：指定每個處理緩衝區的大小（必須是 256、512、1024、2048 等 2 的次方）。
- `numberOfInputChannels`：輸入通道的數量（通常為 1 或 2）。
- `numberOfOutputChannels`：輸出通道的數量（通常為 1 或 2）。

### 事件
`ScriptProcessorNode` 提供了 `onaudioprocess` 事件，這個事件在音頻處理時會被觸發。用戶需要提供一個函數，該函數將接收音頻數據進行處理。

## 範例
以下是簡單的使用範例，展示如何創建和使用 `ScriptProcessorNode`：

```javascript
// 獲取音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 ScriptProcessorNode
const bufferSize = 4096;
const scriptProcessor = audioContext.createScriptProcessor(bufferSize, 1, 1);

// 設置音頻處理函數
scriptProcessor.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer;
    const outputBuffer = event.outputBuffer;

    // 複製音頻數據
    for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
        const inputData = inputBuffer.getChannelData(channel);
        const outputData = outputBuffer.getChannelData(channel);

        for (let sample = 0; sample < inputBuffer.length; sample++) {
            // 將輸入數據直接傳遞到輸出
            outputData[sample] = inputData[sample];
        }
    }
};

// 將 ScriptProcessorNode 連接到音頻上下文的輸出
scriptProcessor.connect(audioContext.destination);
```

## 解釋
使用 `ScriptProcessorNode` 時，開發者應注意以下幾點：
- **性能考量**：由於 JavaScript 的單線程特性，重的計算會導致音頻的中斷或延遲。應盡量把計算簡化或移至 Web Worker。
- **音頻延遲**：`ScriptProcessorNode` 可能會引入音頻延遲，尤其是在處理高緩衝區大小時，這會影響音頻的即時性。
- **過時的 API**：`ScriptProcessorNode` 在某些情況下被認為是過時的，建議使用 `AudioWorklet`，因為其提供更好的性能和靈活性。

## 一句總結
`ScriptProcessorNode` 是 Web Audio API 中一個強大的工具，用於自定義音頻處理，但需注意性能和延遲問題。