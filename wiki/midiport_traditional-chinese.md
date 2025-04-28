<!--
Meta Description: # MIDIPort：JavaScript 中的 MIDI 端口接口 ## 摘要 MIDIPort 是一個在 Web MIDI API 中的重要接口，允許您連接和操作 MIDI 裝置，支持音樂創作和互動式音樂應用。 ## 文檔 ### 目的 MIDIPort 接口代表一個 MIDI 端口，無論是輸入...
Meta Keywords: midi, midiport, api, web, output
-->

# MIDIPort：JavaScript 中的 MIDI 端口接口

## 摘要
MIDIPort 是一個在 Web MIDI API 中的重要接口，允許您連接和操作 MIDI 裝置，支持音樂創作和互動式音樂應用。

## 文檔
### 目的
MIDIPort 接口代表一個 MIDI 端口，無論是輸入還是輸出。這使得開發者可以與 MIDI 裝置進行通訊，發送和接收 MIDI 訊息，從而實現音樂創作、控制合成器等功能。

### 使用方法
要使用 MIDIPort，首先需要啟用 Web MIDI API。檢查瀏覽器是否支持此 API，然後使用 `navigator.requestMIDIAccess()` 方法獲取 MIDI 訪問權限，並從中獲取 MIDIPort。

### 詳細說明
- **屬性**：
  - `id`：端口的唯一標識符。
  - `name`：端口的名稱。
  - `type`：端口類型，可能是 'input' 或 'output'。
  - `state`：端口的當前狀態，可能是 'connected' 或 'disconnected'。

- **方法**：
  - `send(data, timestamp)`：發送 MIDI 訊息，`data` 是一個包含 MIDI 數據的數組，`timestamp` 是可選的時間戳。
  - `close()`：關閉端口（僅適用於輸出端口）。

## 示例
以下是基本用法示例，展示如何使用 MIDIPort 來發送 MIDI 訊息：

```javascript
// 獲取 MIDI 訪問權限
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    // 遍歷所有輸出端口
    outputs.forEach(function(output) {
        console.log(output.name); // 顯示端口名稱
        // 發送 MIDI 訊息
        output.send([144, 60, 0]); // 發送一個音符開啟訊息
    });
});
```

## 解釋
在使用 MIDIPort 時，需要注意以下幾點：
- 需要確保用戶的瀏覽器支持 Web MIDI API。
- 使用 `navigator.requestMIDIAccess()` 時，可能需要用戶授權才能訪問 MIDI 裝置。
- 發送 MIDI 訊息時，數據格式必須正確，例如，音符開啟訊息應為 `[144, 音符號, 音量]`。

## 一句總結
MIDIPort 是 Web MIDI API 中的接口，能夠用於連接和操作 MIDI 裝置以支持音樂相關應用。