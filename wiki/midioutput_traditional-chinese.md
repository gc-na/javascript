<!--
Meta Description: # MIDIOutput：JavaScript 中的 MIDI 輸出接口 ## 概述 MIDIOutput 是一個 JavaScript 接口，用於處理 MIDI 訊號的輸出，允許開發者向 MIDI 設備發送訊號，從而控制音樂合成器、數位音樂工作站和其他音樂相關設備。 ## 文檔 ### 目的 MI...
Meta Keywords: midi, midioutput, const, outputs, javascript
-->

# MIDIOutput：JavaScript 中的 MIDI 輸出接口

## 概述
MIDIOutput 是一個 JavaScript 接口，用於處理 MIDI 訊號的輸出，允許開發者向 MIDI 設備發送訊號，從而控制音樂合成器、數位音樂工作站和其他音樂相關設備。

## 文檔
### 目的
MIDIOutput 的主要目的是提供一個簡單的方式讓開發者可以透過 Web 瀏覽器與 MIDI 設備進行互動，實現音樂創作和控制。

### 使用方法
在使用 MIDIOutput 之前，必須先獲取 MIDI 瀏覽器 API 的支援。以下是使用 MIDIOutput 的基本步驟：

1. **請求 MIDI 訪問權限**：
   使用 `navigator.requestMIDIAccess()` 來請求 MIDI 訪問權限。

2. **獲取 MIDIOutput**：
   從 MIDI 訪問對象中獲取可用的輸出裝置。

3. **發送 MIDI 訊號**：
   使用 `send()` 方法將 MIDI 訊號發送到指定的 MIDI 裝置。

### 詳細說明
- **方法**：
  - `send(data: Uint8Array | Array<number>, timestamp?: number)`: 此方法用於發送 MIDI 訊號。`data` 參數是一個包含 MIDI 訊號的數組，`timestamp` 參數是可選的，指定訊號發送的時間。

- **屬性**：
  - `id`: 返回 MIDI 輸出裝置的唯一識別碼。
  - `name`: 返回 MIDI 輸出裝置的名稱。

## 範例
以下是一些基本的使用範例：

### 基本範例
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const output = outputs.get('YOUR_OUTPUT_DEVICE_ID'); // 替換為實際的裝置 ID

    // 發送中音 C
    const noteOnMessage = [0x90, 60, 0x7f]; // 0x90 表示 Note On，60 是音符編號，0x7f 是力度
    output.send(noteOnMessage);
});
```

### 延遲發送範例
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const output = outputs.get('YOUR_OUTPUT_DEVICE_ID'); // 替換為實際的裝置 ID

    // 0.5 秒後發送中音 C
    setTimeout(() => {
        const noteOffMessage = [0x80, 60, 0x40]; // 0x80 表示 Note Off
        output.send(noteOffMessage);
    }, 500);
});
```

## 解釋
- **常見陷阱**：
  - 當未獲得 MIDI 訪問權限時，任何 MIDI 操作都會失敗，因此確保在使用前請求相應的權限。
  - 在發送訊號之前，確認所用的 MIDI 裝置 ID 是正確的，否則訊號將無法到達指定的設備。

- **注意事項**：
  - 不同的 MIDI 裝置對於訊號的響應可能有所不同，開發者應該根據實際情況進行調整。
  - 一些瀏覽器可能對 MIDI API 的支持有限，建議使用最新版本的瀏覽器。

## 一句總結
MIDIOutput 是一個強大的 JavaScript 接口，能夠讓開發者輕鬆地向 MIDI 設備發送訊號，實現音樂創作的互動性。