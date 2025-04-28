<!--
Meta Description: # MIDIMessageEvent：JavaScript中的MIDI消息事件 ## 簡介 MIDIMessageEvent 是一種在 Web MIDI API 中使用的事件對象，用於表示來自 MIDI 設備的消息。它使開發者能夠接收和處理 MIDI 數據，實現音樂應用程式和互動式音樂體驗。 ## ...
Meta Keywords: midi, midimessageevent, inputs, function, onmidisuccess
-->

# MIDIMessageEvent：JavaScript中的MIDI消息事件

## 簡介
MIDIMessageEvent 是一種在 Web MIDI API 中使用的事件對象，用於表示來自 MIDI 設備的消息。它使開發者能夠接收和處理 MIDI 數據，實現音樂應用程式和互動式音樂體驗。

## 文檔
### 目的
MIDIMessageEvent 對象的主要目的是提供一種方式來處理來自 MIDI 設備的消息。當 MIDI 設備發送消息時，瀏覽器會觸發此事件，以便開發者能夠響應這些消息。

### 使用方法
要使用 MIDIMessageEvent，開發者首先需要獲取 MIDI 設備的訪問權限，然後可以通過事件監聽器來接收事件。

#### 基本語法
```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.onmidimessage = handleMIDIMessage;
    });
}

function handleMIDIMessage(event) {
    const midiMessageEvent = event; // MIDIMessageEvent 對象
    // 處理 MIDI 訊息
}
```

### 詳細說明
- **屬性**：
    - `data`: 包含 MIDI 消息的 Uint8Array。
    - `timeStamp`: 表示事件發生的時間戳。
  
- **事件類型**：
    - `midimessage`: 當 MIDI 設備發送消息時觸發。

## 範例
以下是一個簡單的範例，顯示如何使用 MIDIMessageEvent 來接收和處理 MIDI 訊息：

```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.onmidimessage = function(event) {
            const message = event.data;
            console.log("收到 MIDI 訊息:", message);
        };
    });
}

function onMIDIFailure() {
    console.error("無法獲取 MIDI 設備");
}
```

## 解釋
在使用 MIDIMessageEvent 時，開發者需要注意以下幾點：
- **瀏覽器支持**：並非所有瀏覽器都支持 Web MIDI API，請確認目標瀏覽器的兼容性。
- **設備連接**：在嘗試接收 MIDI 消息之前，確保 MIDI 設備已正確連接並可用。
- **安全性**：某些瀏覽器需要用戶授權才能訪問 MIDI 設備，請遵循相關安全指南。

## 一行總結
MIDIMessageEvent 是一種用於處理來自 MIDI 設備的消息的事件對象，使開發者能夠創建互動式音樂應用程式。