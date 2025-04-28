<!--
Meta Description: # ScriptProcessorNode: JavaScript 音頻處理的強大工具 ## 概述 `ScriptProcessorNode` 是 Web Audio API 中的一個重要組件，允許開發者進行音頻數據的即時處理和生成，特別適合需要低延遲音頻處理的應用。 ## 文檔 `ScriptPr...
Meta Keywords: scriptprocessornode, audiocontext, const, event, javascript
-->

# ScriptProcessorNode: JavaScript 音頻處理的強大工具

## 概述
`ScriptProcessorNode` 是 Web Audio API 中的一個重要組件，允許開發者進行音頻數據的即時處理和生成，特別適合需要低延遲音頻處理的應用。

## 文檔
`ScriptProcessorNode` 主要用於音頻流的自定義處理。它提供了一個可以編寫 JavaScript 代碼的接口，來處理音頻樣本。這個節點可以用來創建音頻效果、合成音頻或進行音頻分析。

### 用途
- 實時音頻處理
- 自定義音效創建
- 音頻數據的分析與修改

### 使用方法
要創建一個 `ScriptProcessorNode`，你需要有一個 `AudioContext` 實例，並使用其 `createScriptProcessor` 方法。這個方法接受三個參數：緩衝區大小、輸入通道數和輸出通道數。

```javascript
const audioContext = new AudioContext();
const scriptProcessorNode = audioContext.createScriptProcessor(bufferSize, inputChannels, outputChannels);
```

使用 `onaudioprocess` 事件來處理音頻數據：

```javascript
scriptProcessorNode.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer;
    const outputBuffer = event.outputBuffer;

    // 在這裡進行音頻處理
};
```

## 範例
以下是一個簡單的使用 `ScriptProcessorNode` 的範例，將音頻信號反轉：

```javascript
const audioContext = new AudioContext();
const scriptProcessorNode = audioContext.createScriptProcessor(4096, 1, 1);

scriptProcessorNode.onaudioprocess = function(event) {
    const input = event.inputBuffer.getChannelData(0);
    const output = event.outputBuffer.getChannelData(0);

    for (let i = 0; i < input.length; i++) {
        output[i] = input[input.length - i - 1]; // 反轉信號
    }
};

navigator.mediaDevices.getUserMedia({ audio: true })
    .then(function(stream) {
        const source = audioContext.createMediaStreamSource(stream);
        source.connect(scriptProcessorNode);
        scriptProcessorNode.connect(audioContext.destination);
    });
```

## 解釋
使用 `ScriptProcessorNode` 時，有一些常見的陷阱和注意事項：

1. **延遲問題**：`ScriptProcessorNode` 的緩衝區大小會影響延遲，較大的緩衝區會導致較高的延遲。
2. **性能考量**：在 `onaudioprocess` 事件中進行複雜計算可能會導致音頻中斷，因此應保持處理簡單高效。
3. **已被標記為過時**：雖然 `ScriptProcessorNode` 在某些情況下仍然有效，但建議使用 `AudioWorklet` 進行更現代的音頻處理。

## 一句總結
`ScriptProcessorNode` 是 Web Audio API 中一個強大的節點，用於實時音頻處理和生成，適合需要低延遲音頻輸出的應用。