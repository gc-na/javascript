<!--
Meta Description: # MIDIInputMap：JavaScript 中的 MIDI 輸入映射功能 ## 概述 MIDIInputMap 是一個與 Web MIDI API 相關的 JavaScript 功能，允許開發者獲取和管理 MIDI 輸入裝置的映射。這對於音樂應用和交互式媒體項目尤為重要，因為它使開發者能夠靈...
Meta Keywords: midi, midiinputmap, inputs, input, javascript
-->

# MIDIInputMap：JavaScript 中的 MIDI 輸入映射功能

## 概述
MIDIInputMap 是一個與 Web MIDI API 相關的 JavaScript 功能，允許開發者獲取和管理 MIDI 輸入裝置的映射。這對於音樂應用和交互式媒體項目尤為重要，因為它使開發者能夠靈活地處理 MIDI 訊號。

## 文檔
### 目的
MIDIInputMap 的主要目的是提供一種結構化的方式來訪問和處理 MIDI 輸入裝置所發送的數據。通過此功能，開發者可以輕鬆地將 MIDI 裝置的訊號映射到應用程式中的不同操作。

### 使用方法
要使用 MIDIInputMap，首先需要確保瀏覽器支持 Web MIDI API。然後，可以通過 `navigator.requestMIDIAccess()` 方法獲取 MIDI 存取權，接著可以使用 `inputs` 屬性來獲取所有的 MIDI 輸入裝置，並且可以使用 `MIDIInputMap` 來管理這些裝置的映射。

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        console.log(`MIDI Input: ${input.name}`);
    });
});
```

### 詳細資訊
MIDIInputMap 允許開發者根據需要選擇特定的 MIDI 裝置並設置相應的事件監聽器，以便從這些裝置中接收數據。開發者可以使用 `input.addEventListener()` 方法為每個 MIDI 輸入裝置設置回調函數，處理來自裝置的 MIDI 訊號。

## 範例
以下是一個簡單的範例，展示如何使用 MIDIInputMap 獲取並處理 MIDI 輸入裝置的訊號：

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    
    inputs.forEach((input) => {
        input.onmidimessage = function(message) {
            console.log(`Received MIDI message: ${message.data}`);
        };
    });
}).catch(function(error) {
    console.error(`Error accessing MIDI devices: ${error}`);
});
```

## 說明
在使用 MIDIInputMap 時，開發者需要注意以下幾點：

1. **瀏覽器支持**：並非所有瀏覽器都支持 Web MIDI API，開發者應提前確認目標瀏覽器是否支持此功能。
2. **裝置權限**：用戶需要授予應用程式對 MIDI 裝置的訪問權限，否則應用將無法接收到任何 MIDI 訊息。
3. **訊息格式**：MIDI 訊息格式為數組，開發者需了解 MIDI 訊息的結構，以便進行正確處理。

## 單行摘要
MIDIInputMap 是一個 JavaScript 功能，允許開發者獲取和管理 MIDI 輸入裝置的映射，方便音樂應用的開發。