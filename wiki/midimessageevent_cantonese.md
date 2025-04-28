<!--
Meta Description: # MIDIMessageEvent：JavaScript 中的 MIDI 消息事件 ## 概述 MIDIMessageEvent 是 Web MIDI API 中的一個事件類型，用於表示 MIDI 消息的接收。這個事件能夠讓開發者在 JavaScript 應用程式中接收和處理 MIDI 數據，從而...
Meta Keywords: midi, midimessageevent, javascript, access, inputs
-->

# MIDIMessageEvent：JavaScript 中的 MIDI 消息事件

## 概述
MIDIMessageEvent 是 Web MIDI API 中的一個事件類型，用於表示 MIDI 消息的接收。這個事件能夠讓開發者在 JavaScript 應用程式中接收和處理 MIDI 數據，從而實現音樂應用程式的互動性。

## 文檔
### 目的
MIDIMessageEvent 的主要目的是在 Web 應用程式中提供 MIDI 訊息的實時接收功能。這使得開發者能夠創建交互式音樂應用程式，並與 MIDI 設備進行溝通。

### 使用方法
要使用 MIDIMessageEvent，開發者需首先確保瀏覽器支持 Web MIDI API。接著，可以通過 MIDI 接口監聽 MIDI 消息事件，當有新的 MIDI 消息到達時，就會產生一個 MIDIMessageEvent 事件。

### 詳細信息
- **屬性**：
  - `data`: 一個 Uint8Array 包含 MIDI 消息的數據。
  - `timeStamp`: 一個時間戳，表示事件發生的時間。

- **事件監聽**：
  使用 `addEventListener` 方法來監聽 MIDI 消息事件。例如：
  ```javascript
  navigator.requestMIDIAccess().then((access) => {
      access.inputs.forEach((input) => {
          input.addEventListener('midimessage', (event) => {
              // 在這裡處理 MIDIMessageEvent
          });
      });
  });
  ```

## 範例
以下是如何使用 MIDIMessageEvent 的基本範例：

```javascript
navigator.requestMIDIAccess().then((access) => {
    const inputs = access.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = (event) => {
            const message = event.data;
            console.log(`MIDI Message: ${message}`);
        };
    });
}).catch((error) => {
    console.error('MIDI Access failed:', error);
});
```

## 解釋
在使用 MIDIMessageEvent 時，開發者需要注意以下幾點：
- 確保用戶授權訪問 MIDI 設備，否則無法接收消息。
- 不同的 MIDI 設備可能會發送不同格式的消息，需根據具體情況處理。
- 使用 `Uint8Array` 來解析 MIDI 數據，這對於理解消息的內容至關重要。

## 一句總結
MIDIMessageEvent 是一個重要的事件類型，允許 JavaScript 開發者接收和處理 MIDI 消息，從而創造出豐富的音樂應用體驗。