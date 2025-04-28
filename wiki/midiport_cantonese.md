<!--
Meta Description: # MIDIPort：JavaScript 中的 MIDI 端口操作 ## 概述 MIDIPort 是 Web MIDI API 的一部分，允許網頁應用程式與 MIDI 設備進行互動。通過 MIDIPort，開發者可以讀取和發送 MIDI 訊息，從而實現音樂創作、演奏和控制。 ## 文檔 ### 目...
Meta Keywords: midi, midiport, javascript, inputs, outputs
-->

# MIDIPort：JavaScript 中的 MIDI 端口操作

## 概述
MIDIPort 是 Web MIDI API 的一部分，允許網頁應用程式與 MIDI 設備進行互動。通過 MIDIPort，開發者可以讀取和發送 MIDI 訊息，從而實現音樂創作、演奏和控制。

## 文檔
### 目的
MIDIPort 代表一個 MIDI 端口，可以是輸入端或輸出端。這個接口使得 JavaScript 開發者能夠輕鬆地與各種 MIDI 設備進行通信。

### 使用方法
要使用 MIDIPort，首先需要訪問 Web MIDI API，並獲取可用的 MIDI 端口。以下是基本使用步驟：

1. **請求 MIDI 設備的權限**：
   使用 `navigator.requestMIDIAccess()` 方法請求對 MIDI 設備的訪問權限。

2. **獲取端口列表**：
   獲取 MIDI 端口的列表，並通過 `inputs` 和 `outputs` 屬性訪問可用的輸入和輸出端口。

3. **發送和接收 MIDI 訊息**：
   通過所選擇的端口發送和接收 MIDI 訊息，例如使用 `send()` 方法來發送訊息。

### 詳細說明
- **屬性**：
  - `id`：端口的唯一標識符。
  - `name`：端口的名稱。
  - `type`：端口的類型（`input` 或 `output`）。
  - `state`：端口的當前狀態（`connected` 或 `disconnected`）。

- **方法**：
  - `send(data, timestamp)`：發送 MIDI 訊息。
  - `close()`：關閉端口（僅適用於輸出端口）。

## 範例
### 獲取 MIDI 設備
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        console.log(`Input port: ${input.name}`);
    });
});
```

### 發送 MIDI 訊息
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    const output = outputs.get('your-output-port-id'); // 替換為實際的端口 ID
    const noteOnMessage = [0x90, 60, 0x7f]; // 音符開啟訊息
    output.send(noteOnMessage);
});
```

## 解釋
在使用 MIDIPort 時，開發者應注意以下幾點：
- 確保用戶已授權使用 MIDI 設備，否則不能獲取端口列表。
- 在發送訊息時，必須遵循 MIDI 訊息格式，例如音符開啟訊息必須包含通道、音符和力度。
- 使用 `close()` 方法關閉輸出端口時，請確認已不再需要該端口，以防止資源浪費。

## 一句總結
MIDIPort 允許 JavaScript 應用程式方便地與 MIDI 設備進行互動，支持音樂創作和控制。