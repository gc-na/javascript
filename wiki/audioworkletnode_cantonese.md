<!--
Meta Description: # AudioWorkletNode：JavaScript 音頻處理的強大工具 ## 概述 `AudioWorkletNode` 是 Web Audio API 的一部分，允許開發者在瀏覽器中創建高效的音頻處理節點。這個功能使得開發者能夠自定義音頻處理算法，實現複雜的音頻效果和合成器。 ## 文檔 ...
Meta Keywords: audioworkletnode, audiocontext, audioworkletprocessor, javascript, audioworklet
-->

# AudioWorkletNode：JavaScript 音頻處理的強大工具

## 概述
`AudioWorkletNode` 是 Web Audio API 的一部分，允許開發者在瀏覽器中創建高效的音頻處理節點。這個功能使得開發者能夠自定義音頻處理算法，實現複雜的音頻效果和合成器。

## 文檔
`AudioWorkletNode` 的主要目的是提供一個可以執行自定義音頻處理的環境。它在 JavaScript 的工作上下文中運行，並且能夠在實時音頻處理中達到低延遲的效果。這對於需要精細音頻控制的應用（如音樂編輯器和遊戲音效）特別有用。

### 使用方式
使用 `AudioWorkletNode` 的基本步驟如下：

1. **創建 AudioWorkletProcessor**：首先需要創建一個繼承自 `AudioWorkletProcessor` 的類，並實現其 `process` 方法。
2. **加載 AudioWorkletModule**：使用 `AudioContext.audioWorklet.addModule()` 方法來加載自定義的 AudioWorklet 模組。
3. **實例化 AudioWorkletNode**：在 `AudioContext` 中創建 `AudioWorkletNode` 的實例並將其連接到音頻圖中。

### 代碼示例
以下是如何使用 `AudioWorkletNode` 的基本示例：

```javascript
// 定義 AudioWorkletProcessor
class MyAudioProcessor extends AudioWorkletProcessor {
    process(inputs, outputs, parameters) {
        const output = outputs[0];
        for (let i = 0; i < output.length; i++) {
            output[i].fill(0); // 清空輸出
        }
        return true; // 繼續處理
    }
}

// 加載 AudioWorklet 模組
const audioContext = new AudioContext();
audioContext.audioWorklet.addModule('my-audio-processor.js').then(() => {
    const myNode = new AudioWorkletNode(audioContext, 'my-audio-processor');
    // 將節點連接到音頻圖
    myNode.connect(audioContext.destination);
});
```

## 解釋
在使用 `AudioWorkletNode` 時，有幾個常見的問題和注意事項：

- **性能考量**：`AudioWorkletNode` 在低延遲音頻處理中非常高效，但需要確保處理過程中的算法不會過於複雜，否則可能導致性能下降。
- **跨執行緒**：`AudioWorkletProcessor` 在一個獨立的執行緒中運行，這意味著不能直接訪問 DOM 或者使用某些全局變量。
- **參數傳遞**：如果需要在處理過程中調整參數，可以使用 `AudioParam` 來進行參數的傳遞和調整。

## 一句總結
`AudioWorkletNode` 使得開發者能夠在 JavaScript 中創建自定義音頻處理節點，實現高效和靈活的音頻效果。