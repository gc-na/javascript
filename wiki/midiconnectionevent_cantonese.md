<!--
Meta Description: # MIDIConnectionEvent：JavaScript 中的 MIDI 連接事件 ## 概述 MIDIConnectionEvent 是一個在 Web MIDI API 中使用的事件類型，當 MIDI 設備的連接狀態改變時會觸發。這使得開發者可以即時獲取 MIDI 設備的連接和斷開情況，對...
Meta Keywords: midi, midiconnectionevent, api, javascript, web
-->

# MIDIConnectionEvent：JavaScript 中的 MIDI 連接事件

## 概述
MIDIConnectionEvent 是一個在 Web MIDI API 中使用的事件類型，當 MIDI 設備的連接狀態改變時會觸發。這使得開發者可以即時獲取 MIDI 設備的連接和斷開情況，對於音樂應用程式的開發具有重要意義。

## 文件說明
### 目的
MIDIConnectionEvent 旨在提供一個簡單的接口，讓開發者能夠監控 MIDI 設備的連接狀態，從而能夠動態地更新應用程式的行為以適應設備變化。

### 使用方法
MIDIConnectionEvent 是通過 MIDI API 自動生成的事件，使用者可以通過在某個 MIDI 連接的事件監聽器中捕捉這些事件。

#### 屬性
- **type**: 事件的類型，通常值為 "statechange"。
- **port**: 觸發事件的 MIDI 端口，這是 MIDIPort 的實例。

### 相關方法
要使用 MIDIConnectionEvent，開發者需先獲取 MIDI 硬件的支持，然後可以通過 MIDI API 獲取 MIDI 端口的列表。在此基礎上可以添加事件監聽器來捕捉 MIDIConnectionEvent。

## 範例
以下是如何使用 MIDIConnectionEvent 的基本範例：

```javascript
// 確認瀏覽器支持 Web MIDI API
if (navigator.requestMIDIAccess) {
    navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
}

function onMIDISuccess(midiAccess) {
    // 獲取所有 MIDI 端口
    const inputs = midiAccess.inputs;
    
    // 監聽 MIDI 端口的連接狀態變化
    inputs.forEach((input) => {
        input.onstatechange = (event) => {
            console.log(`MIDI 端口狀態改變: ${event.port.name} 已${event.port.state}`);
        };
    });
}

function onMIDIFailure() {
    console.error("無法獲取 MIDI 訪問權限");
}
```

## 解釋
使用 MIDIConnectionEvent 時，開發者需要注意以下幾點：
- 確保你在支持 Web MIDI API 的環境中執行代碼。
- 事件僅在連接狀態變化時觸發，因此需要適當地管理 `onstatechange` 事件的處理函數，以避免重複處理。
- 對於許多 MIDI 設備，連接和斷開的速度可能很快，因此需要考慮如何有效地反映這些變化。

## 總結
MIDIConnectionEvent 是一個重要的事件類型，能夠幫助開發者在 JavaScript 中有效地監控與 MIDI 設備的連接狀態變化。