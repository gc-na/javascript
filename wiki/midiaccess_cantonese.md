<!--
Meta Description: # MIDIAccess：JavaScript 中的媒體存取介面 ## 概述 MIDIAccess 是一個 JavaScript 介面，允許開發者訪問 MIDI 設備，促進音樂和音效應用的開發。透過 MIDIAccess，開發者可以獲取 MIDI 設備的列表、監聽 MIDI 訊息，以及發送控制訊號。...
Meta Keywords: midi, midiaccess, inputs, javascript, console
-->

# MIDIAccess：JavaScript 中的媒體存取介面

## 概述
MIDIAccess 是一個 JavaScript 介面，允許開發者訪問 MIDI 設備，促進音樂和音效應用的開發。透過 MIDIAccess，開發者可以獲取 MIDI 設備的列表、監聽 MIDI 訊息，以及發送控制訊號。

## 文件說明
### 目的
MIDIAccess 主要用於讓網頁應用程式與 MIDI 設備互動，支持音樂創作、音效設計和其他相關應用。

### 使用方法
要使用 MIDIAccess，開發者需要通過 `navigator.requestMIDIAccess()` 方法請求存取 MIDI 設備。該方法返回一個 Promise，解析為 MIDIAccess 物件。

### 詳細資料
- **方法**：
  - `navigator.requestMIDIAccess()`: 請求存取 MIDI 設備，返回 MIDIAccess 物件。
- **物件屬性**：
  - `inputs`: 返回一個 MIDIInputMap，包含所有可用的 MIDI 輸入設備。
  - `outputs`: 返回一個 MIDIOutputMap，包含所有可用的 MIDI 輸出設備。
  
- **事件**：
  - `statechange`: 當 MIDI 設備的狀態改變時觸發。

## 範例
以下是使用 MIDIAccess 的基本範例：

```javascript
navigator.requestMIDIAccess()
  .then(function(midiAccess) {
    console.log('MIDI 連接成功！');
    
    // 列出所有 MIDI 輸入設備
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
      console.log(`輸入設備: ${input.name}`);
    });

    // 監聽 MIDI 訊息
    inputs.forEach(input => {
      input.onmidimessage = function(message) {
        console.log(`收到 MIDI 訊息: ${message.data}`);
      };
    });
  })
  .catch(function(error) {
    console.error('無法獲取 MIDI 設備:', error);
  });
```

## 解釋
在使用 MIDIAccess 時，有幾個常見的陷阱需要注意：
- 確保使用 HTTPS 協議，因為大多數瀏覽器僅在安全的環境下允許使用 MIDI 功能。
- 有些設備可能不支持特定的 MIDI 訊息格式，開發者需要進行相應的錯誤處理。
- 當使用 `onmidimessage` 事件時，記得檢查訊息的格式和內容，以避免不必要的錯誤。

## 一句總結
MIDIAccess 是 JavaScript 中的強大工具，讓開發者能夠輕鬆存取和控制 MIDI 設備。