<!--
Meta Description: # MIDIOutput 在 JavaScript 中的應用 ## 簡介 MIDIOutput 是一個 JavaScript API，用於與 MIDI 設備進行通信，讓開發者可以發送 MIDI 訊息給音樂硬體或軟體。 ## 文檔 ### 目的 MIDIOutput 主要用於發送 MIDI 訊息，這些...
Meta Keywords: midi, midioutput, send, javascript, outputs
-->

# MIDIOutput 在 JavaScript 中的應用

## 簡介
MIDIOutput 是一個 JavaScript API，用於與 MIDI 設備進行通信，讓開發者可以發送 MIDI 訊息給音樂硬體或軟體。

## 文檔
### 目的
MIDIOutput 主要用於發送 MIDI 訊息，這些訊息可以控制音樂合成器、采樣器及其他 MIDI 兼容裝置。

### 使用方法
要使用 MIDIOutput，開發者首先需要獲取可用的 MIDI 輸出裝置，然後可以通過該裝置發送訊息。這通常涉及以下步驟：

1. **請求 MIDI 訪問權限**：使用 `navigator.requestMIDIAccess()` 來請求 MIDI 訪問權限。
2. **獲取 MIDI 輸出**：通過 `MIDIAccess.outputs` 獲取可用的輸出裝置。
3. **發送 MIDI 訊息**：使用 `send()` 方法發送 MIDI 訊息。

### 詳細說明
以下是 MIDIOutput 使用的一些關鍵細節：

- **MIDI 訊息格式**：MIDI 訊息通常包括一個狀態字節和一到兩個數據字節。例如，音符開啟的訊息格式為 `[0x90, noteNumber, velocity]`。
- **send() 方法**：`send(data, timestamp)` 方法可以發送 MIDI 訊息，其中 `data` 是一個包含字節的 Uint8Array，`timestamp` 是可選的時間戳。
- **異步操作**：MIDI 訪問是異步的，因此應確保在獲取 MIDI 設備後再進行訊息發送。

## 範例
以下是一些 MIDIOutput 的基本使用範例：

```javascript
// 請求 MIDI 訪問
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const outputs = midiAccess.outputs;
    // 獲取第一個可用的 MIDI 輸出
    const output = outputs.values().next().value;

    // 發送音符開啟訊息
    if (output) {
        output.send([0x90, 60, 0x7f]); // 開啟音符 C4
        output.send([0x80, 60, 0x40]); // 關閉音符 C4
    }
}

function onMIDIFailure() {
    console.error('無法獲取 MIDI 訪問權限');
}
```

## 解釋
在使用 MIDIOutput 時，開發者需要注意以下幾點：

- **設備兼容性**：並非所有瀏覽器都支持 MIDI API，確保你的用戶使用兼容的瀏覽器。
- **音訊延遲**：MIDI 訊息的發送可能會有延遲，這在即時音樂應用中可能會影響性能。
- **錯誤處理**：確保在請求 MIDI 訪問時處理錯誤，以提供良好的用戶體驗。

## 一句總結
MIDIOutput 是一個強大的 JavaScript API，讓開發者能夠輕鬆地發送 MIDI 訊息給音樂設備。