<!--
Meta Description: # MIDIInput：JavaScript中的MIDI輸入接口 ## 摘要 MIDIInput是Web MIDI API中的一個接口，允許JavaScript應用程式接收來自MIDI設備的輸入數據。它支持即時音樂創作和控制，為Web應用帶來互動性。 ## 文檔 ### 目的 MIDIInput接口...
Meta Keywords: inputs, onmidimessage, function, midi, 請求midi設備訪問
-->

# MIDIInput：JavaScript中的MIDI輸入接口

## 摘要
MIDIInput是Web MIDI API中的一個接口，允許JavaScript應用程式接收來自MIDI設備的輸入數據。它支持即時音樂創作和控制，為Web應用帶來互動性。

## 文檔
### 目的
MIDIInput接口的主要目的是促進Web應用與MIDI設備之間的互動。這使得開發者能夠監聽MIDI信號並進行相應的操作，從而創建音樂應用、遊戲或其他需要音頻控制的應用。

### 使用方法
要使用MIDIInput接口，開發者首先需要獲取MIDI設備的訪問權限，然後可以從中獲取MIDIInput對象。通常的流程如下：

1. **請求MIDI設備訪問**：
   使用`navigator.requestMIDIAccess()`來請求MIDI設備的訪問權限。

2. **獲取MIDI輸入**：
   在成功回調中，透過`inputs`屬性來獲取可用的MIDI輸入設備，然後選擇一個進行監聽。

3. **監聽數據**：
   使用`onmidimessage`事件來接收來自MIDI設備的輸入數據。

### 詳細說明
MIDIInput接口提供了以下重要的屬性和方法：

- `onmidimessage`：當接收到MIDI消息時觸發的事件處理器。
- `id`：MIDI輸入的唯一標識符。
- `name`：MIDI輸入的名稱。

這些屬性和方法可以幫助開發者更方便地處理來自MIDI設備的數據。

## 示例
以下是使用MIDIInput的基本示例：

```javascript
// 請求MIDI設備訪問
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    // 獲取所有MIDI輸入
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        // 監聽MIDI消息
        input.onmidimessage = handleMIDIMessage;
    });
}

function onMIDIFailure() {
    console.error("無法訪問MIDI設備");
}

function handleMIDIMessage(event) {
    console.log(`MIDI消息：${event.data}`);
}
```

## 解釋
在使用MIDIInput時，有幾個常見的陷阱需要注意：

1. **瀏覽器支持**：確認你的瀏覽器支持Web MIDI API，因為並非所有瀏覽器都支持該功能。
2. **設備連接**：確保MIDI設備正確連接並已開啟，否則將無法接收到任何數據。
3. **權限問題**：使用MIDI功能時，瀏覽器可能會要求用戶授予訪問權限，請確保用戶同意。

## 一句總結
MIDIInput接口使JavaScript應用能夠接收和處理來自MIDI設備的輸入數據，為多媒體創作提供了強大的支持。