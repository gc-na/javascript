<!--
Meta Description: # MIDIOutputMap: JavaScript 中的 MIDI 輸出映射 ## 摘要 MIDIOutputMap 是一個用於 JavaScript 的接口，提供對 MIDI 輸出端口的映射，讓開發者可以方便地管理和使用 MIDI 輸出設備。 ## 文檔 MIDIOutputMap 是 Web...
Meta Keywords: midi, midioutputmap, outputs, javascript, 訪問權限
-->

# MIDIOutputMap: JavaScript 中的 MIDI 輸出映射

## 摘要
MIDIOutputMap 是一個用於 JavaScript 的接口，提供對 MIDI 輸出端口的映射，讓開發者可以方便地管理和使用 MIDI 輸出設備。

## 文檔
MIDIOutputMap 是 Web MIDI API 的一部分，旨在讓開發者能夠與 MIDI 輸出設備進行互動。透過這個接口，開發者可以獲取已連接的 MIDI 輸出設備的詳細信息，包括設備名稱、ID 以及其狀態。這對於音樂應用或任何需要 MIDI 數據傳輸的應用程序來說都是非常有用的。

### 目的
MIDIOutputMap 的主要目的是提供一個簡單的方式來存取和使用可用的 MIDI 輸出端口，實現對 MIDI 訊息的傳遞。

### 使用方法
要使用 MIDIOutputMap，開發者需要首先獲取 `navigator.requestMIDIAccess()` 的返回值，然後從中取得 `outputs` 屬性，這會返回一個 MIDIOutputMap 對象。以下是基本的使用步驟：

1. 請求 MIDI 訪問權限：
   ```javascript
   navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
   ```

2. 在成功回調中獲取 MIDIOutputMap：
   ```javascript
   function onMIDISuccess(midiAccess) {
       let outputs = midiAccess.outputs;
       // 使用 outputs
   }
   ```

## 範例
以下是使用 MIDIOutputMap 的基本範例：

```javascript
navigator.requestMIDIAccess()
    .then(midiAccess => {
        const outputs = midiAccess.outputs;
        outputs.forEach(output => {
            console.log(`輸出設備名稱: ${output.name}`);
            console.log(`輸出設備 ID: ${output.id}`);
        });
    })
    .catch(err => {
        console.error("無法獲取 MIDI 訪問權限:", err);
    });
```

在這個範例中，我們請求 MIDI 訪問權限，然後列出所有可用的 MIDI 輸出設備及其名稱和ID。

## 解釋
在使用 MIDIOutputMap 時，有幾個常見的陷阱和注意事項：

1. **權限問題**：確保在安全的上下文中（如 HTTPS 或 localhost）運行代碼，否則可能無法獲取 MIDI 訪問權限。
2. **設備連接狀態**：當設備連接或斷開時，MIDIOutputMap 可能不會自動更新，因此需要監聽 `statechange` 事件以獲取最新狀態。
3. **兼容性**：並非所有瀏覽器均支持 Web MIDI API，開發者應檢查當前瀏覽器的支持情況。

## 一行總結
MIDIOutputMap 是一個 JavaScript 接口，用於方便地管理和使用可用的 MIDI 輸出設備。