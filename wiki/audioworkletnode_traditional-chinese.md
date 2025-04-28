<!--
Meta Description: # AudioWorkletNode：深入了解 JavaScript 的音頻處理功能 ## 摘要 AudioWorkletNode 是 Web Audio API 的一部分，允許開發者創建自定義音頻處理節點，以便在音頻流中進行高效的處理和生成。 ## 文檔 ### 目的 AudioWorkletNo...
Meta Keywords: audioworkletnode, audiocontext, const, processor, channel
-->

# AudioWorkletNode：深入了解 JavaScript 的音頻處理功能

## 摘要
AudioWorkletNode 是 Web Audio API 的一部分，允許開發者創建自定義音頻處理節點，以便在音頻流中進行高效的處理和生成。

## 文檔
### 目的
AudioWorkletNode 旨在提供一種靈活的方式來處理音頻數據，允許開發者在音頻處理的過程中運行自定義的 JavaScript 代碼，以實現更高效的音頻效果和合成。

### 使用方法
要使用 AudioWorkletNode，首先需要創建一個 AudioWorkletProcessor，然後將其加載到 AudioContext。以下是基本的步驟：

1. 創建一個 AudioWorkletProcessor：
```javascript
class MyProcessor extends AudioWorkletProcessor {
    process(inputs, outputs, parameters) {
        const output = outputs[0];
        // 處理音頻數據
        return true; // 返回 true 以繼續處理
    }
}

registerProcessor('my-processor', MyProcessor);
```

2. 在 AudioContext 中加載和使用 AudioWorkletNode：
```javascript
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule('path/to/my-processor.js');

const myNode = new AudioWorkletNode(audioContext, 'my-processor');
audioContext.destination.connect(myNode);
myNode.connect(audioContext.destination);
```

### 詳細說明
- **屬性**：
  - `port`：用於在節點和主線程之間傳遞消息。

- **方法**：
  - `process(inputs, outputs, parameters)`：這是每次音頻處理周期調用的方法。

AudioWorkletNode 的設計使其適合高效的音頻計算，並且能夠在多個音頻流中運行自定義的音頻處理代碼。

## 示例
以下是使用 AudioWorkletNode 的基本示例：

```javascript
// 定義音頻處理器
class GainProcessor extends AudioWorkletProcessor {
    constructor() {
        super();
        this.gainValue = 1;
        this.port.onmessage = (event) => {
            this.gainValue = event.data.gain;
        };
    }

    process(inputs, outputs) {
        const input = inputs[0];
        const output = outputs[0];

        for (let channel = 0; channel < output.length; channel++) {
            for (let i = 0; i < output[channel].length; i++) {
                output[channel][i] = input[channel][i] * this.gainValue;
            }
        }
        return true;
    }
}

registerProcessor('gain-processor', GainProcessor);

// 在主線程中創建 AudioWorkletNode
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule('gain-processor.js');
const gainNode = new AudioWorkletNode(audioContext, 'gain-processor');
```

## 解釋
- **常見問題**：
  - 確保在使用 AudioWorkletNode 之前已經加載了對應的處理器模組。
  - 注意消息傳遞的性能開銷，盡量減少主線程和工作線程之間的通信。

- **注意事項**：
  - AudioWorkletNode 是在主線程之外運行的，這可以減少音頻處理對 UI 的影響。
  - 設計時要考慮到性能和延遲，避免在 `process` 方法中執行重的計算。

## 一句總結
AudioWorkletNode 是一個功能強大的工具，允許開發者在 Web Audio API 中實現自定義的音頻處理，提升音頻應用的性能和靈活性。