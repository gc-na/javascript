<!--
Meta Description: # AudioWorklet：JavaScript 音頻處理的強大工具 ## 摘要 AudioWorklet 是一個用於在瀏覽器中進行高效音訊處理的 JavaScript API，讓開發者能夠創建自定義音訊處理節點，以實現低延遲和高性能的音訊應用。 ## 文件說明 AudioWorklet 是 We...
Meta Keywords: audioworklet, javascript, audiocontext, processor, audioworkletprocessor
-->

# AudioWorklet：JavaScript 音頻處理的強大工具

## 摘要
AudioWorklet 是一個用於在瀏覽器中進行高效音訊處理的 JavaScript API，讓開發者能夠創建自定義音訊處理節點，以實現低延遲和高性能的音訊應用。

## 文件說明
AudioWorklet 是 Web Audio API 的一部分，旨在提供更靈活的音訊處理選項。與傳統的 ScriptProcessorNode 相比，AudioWorklet 提供了更低的延遲和更高的效能，因為它在瀏覽器的音訊處理線程中運行，避免了主線程的干擾。

### 目的
AudioWorklet 使開發者能夠：
- 創建自定義音訊處理節點。
- 在專用的音訊處理線程中運行 JavaScript，以減少延遲。
- 進行複雜的音訊計算和效果處理。

### 使用方法
要使用 AudioWorklet，開發者需要遵循以下步驟：
1. 創建一個 JavaScript 文件，定義自定義的 AudioWorkletProcessor。
2. 在主線程中加載這個 AudioWorklet。
3. 創建 AudioWorkletNode 並將其連接到音訊圖形中。

### 詳細說明
- **創建 AudioWorkletProcessor**：
  ```javascript
  class MyProcessor extends AudioWorkletProcessor {
      process(inputs, outputs, parameters) {
          // 音訊處理邏輯
          return true; // 返回 true 表示持續處理
      }
  }
  registerProcessor('my-processor', MyProcessor);
  ```

- **加載 AudioWorklet**：
  ```javascript
  const audioContext = new AudioContext();
  await audioContext.audioWorklet.addModule('my-processor.js');
  ```

- **使用 AudioWorkletNode**：
  ```javascript
  const myNode = new AudioWorkletNode(audioContext, 'my-processor');
  myNode.connect(audioContext.destination);
  ```

## 示例
### 基本用法示例
以下是簡單的使用範例，展示如何創建一個自定義的 AudioWorkletProcessor，並在音訊上下文中使用它：

```javascript
// my-processor.js
class MyProcessor extends AudioWorkletProcessor {
    process(inputs, outputs) {
        const output = outputs[0];
        for (let channel = 0; channel < output.length; ++channel) {
            const outputChannel = output[channel];
            for (let i = 0; i < outputChannel.length; ++i) {
                outputChannel[i] = Math.random(); // 生成隨機音訊
            }
        }
        return true;
    }
}
registerProcessor('my-processor', MyProcessor);
```

```javascript
// 主文件
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule('my-processor.js');
const myNode = new AudioWorkletNode(audioContext, 'my-processor');
myNode.connect(audioContext.destination);
```

## 說明
### 常見問題與注意事項
- **延遲問題**：由於 AudioWorklet 在音訊線程中運行，開發者需要小心處理延遲。如果處理時間過長，可能會導致音訊卡頓。
- **資料傳輸**：AudioWorkletProcessor 和主線程之間的資料傳輸是透過 MessagePort 實現的，這意味著需要考慮效率和性能。
- **相容性**：雖然大多數現代瀏覽器都支持 AudioWorklet，但仍需檢查相容性，以確保在各平台上正常運行。

## 一句話總結
AudioWorklet 是一個強大的工具，允許開發者在 JavaScript 中創建高效的自定義音訊處理節點，提升音訊應用的性能和響應速度。