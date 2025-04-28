<!--
Meta Description: # MIDIInput：使用 JavaScript 控制 MIDI 裝置的接口 ## 概述 MIDIInput 是 JavaScript Web MIDI API 的一部分，允許開發者與 MIDI 裝置進行互動，接收 MIDI 消息並實現音樂應用程式的即時反應。 ## 文檔 ### 目的 MIDII...
Meta Keywords: midi, midiinput, api, javascript, web
-->

# MIDIInput：使用 JavaScript 控制 MIDI 裝置的接口

## 概述
MIDIInput 是 JavaScript Web MIDI API 的一部分，允許開發者與 MIDI 裝置進行互動，接收 MIDI 消息並實現音樂應用程式的即時反應。

## 文檔
### 目的
MIDIInput 提供了一個接口來接收來自 MIDI 裝置的訊息，讓開發者能夠處理音符、控制變數及其他 MIDI 數據。

### 使用方法
要使用 MIDIInput，必須先獲取 MIDI 裝置列表，然後監聽 MIDIInput 事件。以下是使用此 API 的步驟：

1. 確保瀏覽器支持 Web MIDI API。
2. 使用 `navigator.requestMIDIAccess()` 獲取 MIDI 訪問權限。
3. 使用 `MIDIInput` 對象來接收 MIDI 消息。

### 詳細信息
MIDIInput 對象包含以下主要屬性和方法：

- **onmidimessage**：當接收到 MIDI 消息時觸發的事件。
- **id**：MIDIInput 裝置的唯一識別碼。
- **manufacturer**：MIDI 裝置的製造商名稱。
- **name**：MIDI 裝置的名稱。
- **state**：顯示裝置的連接狀態（已連接或未連接）。

## 範例
以下是使用 MIDIInput 的基本範例：

```javascript
// 請求 MIDI 訪問
navigator.requestMIDIAccess().then(function(midiAccess) {
    // 獲取所有 MIDI 輸入
    const inputs = midiAccess.inputs;

    // 監聽每個 MIDI 輸入
    inputs.forEach((input) => {
        input.onmidimessage = function(message) {
            console.log('Received MIDI message:', message.data);
        };
    });
}).catch(function(err) {
    console.error('MIDI Access Error:', err);
});
```

## 解釋
### 常見問題
- **瀏覽器兼容性**：並非所有瀏覽器都支持 Web MIDI API，請確保使用的瀏覽器版本是最新的。
- **安全性問題**：使用此 API 時需要用 HTTPS 或 localhost，否則將無法訪問 MIDI 裝置。
- **裝置連接狀態**：在連接和斷開 MIDI 裝置時，MIDIInput 的狀態可能會變更，開發者應適時更新界面。

## 總結
MIDIInput 是一個強大的工具，能夠幫助 JavaScript 開發者輕鬆接收和處理來自 MIDI 裝置的輸入數據。