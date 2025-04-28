<!--
Meta Description: # MIDIOutputMap 在 JavaScript 中的應用 ## 簡介 MIDIOutputMap 是一個用於管理 MIDI 輸出設備的 JavaScript API，允許開發者有效地與音樂硬件進行交互。它支持創建音樂應用程序，讓開發者能夠發送 MIDI 訊息至各種音樂設備。 ## 文檔 M...
Meta Keywords: midi, midioutputmap, javascript, outputs, api
-->

# MIDIOutputMap 在 JavaScript 中的應用

## 簡介
MIDIOutputMap 是一個用於管理 MIDI 輸出設備的 JavaScript API，允許開發者有效地與音樂硬件進行交互。它支持創建音樂應用程序，讓開發者能夠發送 MIDI 訊息至各種音樂設備。

## 文檔
MIDIOutputMap 是 Web MIDI API 的一部分，用於獲取可用的 MIDI 輸出設備。此接口提供了一個映射，顯示所有已連接的 MIDI 輸出設備及其屬性。

### 目的
MIDIOutputMap 的主要目的是使 Web 應用程序能夠簡單、靈活地與 MIDI 硬件進行通訊，從而實現音樂創作和編輯功能。

### 使用方法
要使用 MIDIOutputMap，開發者需要首先獲取 MIDI 輸出設備的列表。這通常通過調用 `navigator.requestMIDIAccess()` 方法來完成。當成功獲取 MIDI 訪問權限後，可以使用 `outputs` 屬性來訪問 MIDIOutputMap。

### 詳細信息
- **屬性**:
  - `size`: 返回 MIDIOutputMap 中的輸出設備數量。
  - `get()`: 使用輸出設備的 ID 獲取特定的 MIDIOutput。
  - `forEach()`: 執行回調函數，對 MIDIOutputMap 中的每個輸出設備進行操作。

## 範例
以下是基本的使用範例，展示如何獲取 MIDI 輸出設備並發送訊息。

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    outputs.forEach((output) => {
        console.log(`輸出設備名稱: ${output.name}`);
        // 發送 MIDI 訊息
        output.send([144, 60, 0]); // 發送 Note On 訊息
    });
}).catch((error) => {
    console.error(`無法訪問 MIDI 設備: ${error}`);
});
```

## 解釋
使用 MIDIOutputMap 時要注意以下幾點常見問題：
- 不同的瀏覽器對 Web MIDI API 的支持程度可能不同，建議確認當前使用的瀏覽器是否支持。
- 在某些情況下，可能需要使用 HTTPS 協議來獲取 MIDI 訪問權限，特別是在移動設備上。
- MIDI 訊息的格式和內容必須正確，否則設備可能無法解析或執行。

## 一行總結
MIDIOutputMap 是一個強大的工具，允許 JavaScript 開發者輕鬆管理和發送 MIDI 輸出訊息至音樂設備。