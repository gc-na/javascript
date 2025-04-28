<!--
Meta Description: # AudioProcessingEvent：JavaScript 中的音頻處理事件 ## 概述 `AudioProcessingEvent` 是 Web Audio API 中的一個重要事件類型，主要用於在音頻處理過程中提供對音頻數據的訪問。透過這個事件，開發者能夠直接操作音頻流，以實現自定義的音...
Meta Keywords: const, audiocontext, audioprocessingevent, event, inputbuffer
-->

# AudioProcessingEvent：JavaScript 中的音頻處理事件

## 概述
`AudioProcessingEvent` 是 Web Audio API 中的一個重要事件類型，主要用於在音頻處理過程中提供對音頻數據的訪問。透過這個事件，開發者能夠直接操作音頻流，以實現自定義的音頻效果或進行音頻分析。

## 文檔
`AudioProcessingEvent` 是在音頻上下文中發生的一個事件，當音頻節點需要填充其輸出緩衝區時會被觸發。此事件提供了對音頻數據的訪問，使得開發者可以對音頻進行處理和修改。

### 目的
`AudioProcessingEvent` 主要用於以下目的：
- 允許開發者自定義音頻效果，如音效處理、音頻合成等。
- 提供實時音頻數據的訪問，便於進行音頻分析和可視化。

### 使用
要使用 `AudioProcessingEvent`，需要創建一個 `ScriptProcessorNode` 或 `AudioWorkletNode`，然後監聽其 `audioprocess` 事件。在事件處理函數中，可以訪問音頻緩衝區。

```javascript
const audioContext = new AudioContext();
const scriptNode = audioContext.createScriptProcessor(4096, 1, 1);

scriptNode.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer;
    const outputBuffer = event.outputBuffer;

    for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
        const inputData = inputBuffer.getChannelData(channel);
        const outputData = outputBuffer.getChannelData(channel);

        for (let sample = 0; sample < inputBuffer.length; sample++) {
            outputData[sample] = inputData[sample]; // 直接傳遞輸入到輸出
        }
    }
};

scriptNode.connect(audioContext.destination);
```

## 範例
以下是使用 `AudioProcessingEvent` 的基本範例：

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const scriptProcessor = audioContext.createScriptProcessor(2048, 1, 1);

scriptProcessor.onaudioprocess = function(event) {
    const inputData = event.inputBuffer.getChannelData(0);
    const outputData = event.outputBuffer.getChannelData(0);

    for (let i = 0; i < inputData.length; i++) {
        outputData[i] = inputData[i] * 0.5; // 音量減半
    }
};

navigator.mediaDevices.getUserMedia({ audio: true })
    .then(stream => {
        const source = audioContext.createMediaStreamSource(stream);
        source.connect(scriptProcessor);
        scriptProcessor.connect(audioContext.destination);
    })
    .catch(err => console.error('獲取音頻流失敗:', err));
```

## 解釋
使用 `AudioProcessingEvent` 時，開發者需要注意以下幾點：
- 確保在主線程中運行音頻處理，否則可能導致音頻延遲或中斷。
- 處理音頻數據時，應避免使用異步操作，因為這會影響音頻處理的實時性。
- 使用 `ScriptProcessorNode` 時，需留意其已被 `AudioWorkletNode` 所取代，因此建議使用後者以獲得更好的性能和靈活性。

## 一句總結
`AudioProcessingEvent` 是 JavaScript 中用於實時音頻處理的事件，能讓開發者直接訪問和修改音頻數據。