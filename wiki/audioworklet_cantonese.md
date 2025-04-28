<!--
Meta Description: # AudioWorklet：JavaScript 中音頻處理的強大工具 ## 簡介 AudioWorklet 是 Web Audio API 的一部分，允許開發者在瀏覽器中以低延遲的方式進行音頻處理。它提供了一個靈活的環境，用於創建自定義音頻處理單元，使開發者能夠實現高效的音頻合成和效果處理。 #...
Meta Keywords: audioworklet, audioworkletprocessor, audiocontext, javascript, process
-->

# AudioWorklet：JavaScript 中音頻處理的強大工具

## 簡介
AudioWorklet 是 Web Audio API 的一部分，允許開發者在瀏覽器中以低延遲的方式進行音頻處理。它提供了一個靈活的環境，用於創建自定義音頻處理單元，使開發者能夠實現高效的音頻合成和效果處理。

## 文檔
### 目的
AudioWorklet 的主要目的是提供一個強大的框架，用於處理音頻流，允許開發者在 JavaScript 中編寫自定義音頻節點。這項技術適用於音頻合成、效果應用和實時音頻處理，並且具有低延遲的優勢。

### 使用方法
1. **創建 AudioWorkletProcessor**：開發者需創建一個繼承自 `AudioWorkletProcessor` 的類，並實現其 `process` 方法。
2. **註冊 AudioWorklet**：使用 `AudioWorklet.addModule()` 方法將自定義處理器註冊到 AudioContext。
3. **創建 AudioWorkletNode**：通過 `new AudioWorkletNode()` 創建音頻節點，並將其連接到音頻圖中。

### 詳細說明
- **AudioWorkletProcessor**：這是音頻處理的核心類，負責接收音頻輸入並進行處理。開發者需要實現 `process(inputs, outputs, parameters)` 方法，該方法將在每個音頻樣本周期內被調用。
- **AudioWorkletNode**：這是一種連接到音頻圖的自定義節點。通過這個節點，開發者可以將音頻數據傳遞給 `AudioWorkletProcessor` 進行處理。
- **性能考量**：AudioWorklet 旨在提供低延遲的音頻處理，因此開發者應避免在 `process` 方法中執行耗時的操作，如 DOM 操作或重計算。

## 範例
以下是一個簡單的 AudioWorklet 範例，展示如何創建和使用自定義音頻處理器：

### 創建 AudioWorkletProcessor
```javascript
class MyAudioProcessor extends AudioWorkletProcessor {
    process(inputs, outputs, parameters) {
        const output = outputs[0];
        for (let channel = 0; channel < output.length; ++channel) {
            const outputChannel = output[channel];
            for (let i = 0; i < outputChannel.length; ++i) {
                outputChannel[i] = Math.random(); // 生成隨機音頻
            }
        }
        return true;
    }
}

registerProcessor('my-audio-processor', MyAudioProcessor);
```

### 註冊和使用 AudioWorklet
```javascript
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule('my-audio-processor.js');
const myNode = new AudioWorkletNode(audioContext, 'my-audio-processor');
myNode.connect(audioContext.destination);
```

## 解釋
- **常見陷阱**：在 `process` 方法中，請確保返回 `true`，以保持處理器的運行。如果返回 `false`，將停止處理。
- **執行上下文**：AudioWorklet 在一個獨立的執行上下文中運行，這意味著無法直接訪問 DOM 或全域變數。
- **更新參數**：若需在運行時更新參數，需使用 `AudioParam` 和輸入參數進行設置。

## 一句總結
AudioWorklet 是一種強大的工具，能讓 JavaScript 開發者在瀏覽器中進行高效且低延遲的音頻處理。