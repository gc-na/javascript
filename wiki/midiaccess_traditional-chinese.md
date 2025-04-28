<!--
Meta Description: # MIDIAccess：JavaScript 中的媒體存取接口 ## 概述 MIDIAccess 是一個 JavaScript 接口，允許網頁應用程式訪問 MIDI（音樂數字介面）設備，從而能夠與音樂硬體進行交互。這使得開發者可以創建動態音樂應用程式和遊戲，增強用戶的音樂體驗。 ## 文檔 ###...
Meta Keywords: midi, midiaccess, javascript, navigator, requestmidiaccess
-->

# MIDIAccess：JavaScript 中的媒體存取接口

## 概述
MIDIAccess 是一個 JavaScript 接口，允許網頁應用程式訪問 MIDI（音樂數字介面）設備，從而能夠與音樂硬體進行交互。這使得開發者可以創建動態音樂應用程式和遊戲，增強用戶的音樂體驗。

## 文檔
### 目的
MIDIAccess 提供了一個統一的方式來訪問 MIDI 設備，無論是輸入還是輸出，並且能夠接收和發送 MIDI 訊息。這個接口對於音樂應用開發者來說至關重要，因為它簡化了與 MIDI 硬體的整合過程。

### 用法
要使用 MIDIAccess，您需要調用 `navigator.requestMIDIAccess()` 方法。這個方法返回一個 Promise，解析為一個 MIDIAccess 對象，該對象包含了可用的 MIDI 輸入和輸出設備。

#### 基本語法
```javascript
navigator.requestMIDIAccess().then(successCallback, errorCallback);
```

### 詳細說明
- **successCallback**: 當成功獲得 MIDI 存取權時調用的函數，該函數接收一個 MIDIAccess 對象作為參數。
- **errorCallback**: 當獲取 MIDI 存取權失敗時調用的函數，該函數接收一個錯誤對象作為參數。
- MIDIAccess 物件包含兩個主要屬性：
  - `inputs`: 一個包含所有可用 MIDI 輸入設備的集合。
  - `outputs`: 一個包含所有可用 MIDI 輸出設備的集合。

## 範例
以下是如何使用 MIDIAccess 的基本範例：

### 獲取 MIDI 存取權
```javascript
navigator.requestMIDIAccess().then(
  function(midiAccess) {
    console.log("MIDI Access Granted", midiAccess);
  },
  function() {
    console.error("Could not access MIDI devices.");
  }
);
```

### 列出所有 MIDI 輸入設備
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
  const inputs = midiAccess.inputs;
  inputs.forEach((input) => {
    console.log(input.name);
  });
});
```

### 發送 MIDI 訊息
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
  const outputs = midiAccess.outputs;
  outputs.forEach((output) => {
    output.send([0x90, 60, 0x7f]); // 發送 Note On 訊息
  });
});
```

## 解釋
在使用 MIDIAccess 時，有幾個常見的陷阱需要注意：
- 確保您的瀏覽器支持 Web MIDI API，並且您已經在 HTTPS 環境下運行，因為大多數瀏覽器要求安全上下文。
- 當用戶拒絕 MIDI 存取請求時，應妥善處理錯誤回調，避免應用程式出現異常。
- 有些 MIDI 設備在連接後需要額外的時間來初始化，可能無法立即使用。

## 一句總結
MIDIAccess 是一個強大的 JavaScript 接口，允許開發者輕鬆訪問和操作 MIDI 設備，從而創建互動音樂應用程式。