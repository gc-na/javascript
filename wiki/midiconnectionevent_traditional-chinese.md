<!--
Meta Description: # MIDIConnectionEvent：JavaScript 中的 MIDI 連接事件 ## 摘要 MIDIConnectionEvent 是一個用於處理 MIDI 裝置連接和斷開事件的 JavaScript 介面，對於音樂應用程式開發者來說，這是一個重要的工具，能夠實現即時的 MIDI 裝置管...
Meta Keywords: midi, midiconnectionevent, event, javascript, port
-->

# MIDIConnectionEvent：JavaScript 中的 MIDI 連接事件

## 摘要
MIDIConnectionEvent 是一個用於處理 MIDI 裝置連接和斷開事件的 JavaScript 介面，對於音樂應用程式開發者來說，這是一個重要的工具，能夠實現即時的 MIDI 裝置管理。

## 文檔
### 目的
MIDIConnectionEvent 介面提供了有關 MIDI 裝置連接狀態的訊息，當新的 MIDI 裝置連接或斷開時，相關的事件將會被觸發，使開發者能夠對這些變化做出即時反應。

### 使用方法
要使用 MIDIConnectionEvent，開發者需要先確保瀏覽器支援 Web MIDI API。當 MIDI 裝置連接或斷開時，將會觸發 `statechange` 事件，從而產生 MIDIConnectionEvent 的實例。

```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    midiAccess.onstatechange = handleMIDIConnectionEvent;
}

function onMIDIFailure() {
    console.error('無法獲取 MIDI 訪問權限');
}

function handleMIDIConnectionEvent(event) {
    console.log(`MIDI 裝置 ${event.port.name} ${event.port.state}`);
}
```

### 詳細資訊
MIDIConnectionEvent 主要包含以下屬性：
- **port**：代表引發事件的 MIDI 端口的實例。
- **type**：事件的類型，通常為 "statechange"。

### 事件類型
- **statechange**：當 MIDI 裝置的連接狀態改變時觸發。

## 範例
以下是如何使用 MIDIConnectionEvent 的基本範例：

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    midiAccess.onstatechange = (event) => {
        console.log(event.port.name + ' 的狀態: ' + event.port.state);
    };
}, (err) => {
    console.error('獲取 MIDI 訪問權限失敗:', err);
});
```

在此範例中，一旦 MIDI 裝置連接或斷開，控制台將顯示該裝置的名稱及其狀態。

## 解釋
在使用 MIDIConnectionEvent 時，開發者常見的問題包括：
- **瀏覽器相容性**：並非所有瀏覽器都支援 Web MIDI API，因此在開發之前，必須檢查目標用戶的瀏覽器支援情況。
- **異步行為**：請注意，MIDI 裝置的獲取是異步的，開發者需要處理相應的 Promise，以確保 MIDI 裝置的正確初始化。

## 總結
MIDIConnectionEvent 是一個關鍵的 JavaScript 接口，用於監控 MIDI 裝置的連接狀態，幫助開發者創建更互動的音樂應用程序。