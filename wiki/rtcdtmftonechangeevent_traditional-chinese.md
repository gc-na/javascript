<!--
Meta Description: # RTCDTMFToneChangeEvent：JavaScript 中的 DTMF 音調變更事件 ## 概述 RTCDTMFToneChangeEvent 是一種事件，用於 WebRTC 中，當 DTMF（雙音多頻）音調變更時觸發。這些音調通常用於電話通訊系統中，特別是在撥打電話時輸入數字。 #...
Meta Keywords: dtmf, rtcdtmftonechangeevent, javascript, event, webrtc
-->

# RTCDTMFToneChangeEvent：JavaScript 中的 DTMF 音調變更事件

## 概述
RTCDTMFToneChangeEvent 是一種事件，用於 WebRTC 中，當 DTMF（雙音多頻）音調變更時觸發。這些音調通常用於電話通訊系統中，特別是在撥打電話時輸入數字。

## 文件說明
### 目的
RTCDTMFToneChangeEvent 主要用於監聽和響應 DTMF 音調的變更，這對於需要用戶輸入響應的應用程序（例如自動電話系統）非常重要。

### 使用方式
當 RTCDTMFToneChangeEvent 事件被觸發時，開發者可以使用 `event.tone` 屬性來獲取當前的 DTMF 音調。以下是事件的基本結構：

```javascript
const event = new RTCDTMFToneChangeEvent(type, eventInitDict);
```

### 事件屬性
- **type**: 事件的類型，通常為 `"tonechange"`。
- **eventInitDict**: 一個可選的物件，可以包含以下屬性：
  - **tone**: 觸發事件的 DTMF 音調（例如 `"1"`, `"A"` 等）。

## 範例
以下是如何在 JavaScript 中使用 RTCDTMFToneChangeEvent 的基本範例：

```javascript
const peerConnection = new RTCPeerConnection();

// 添加 DTMF 發送者
const sender = peerConnection.addTrack(audioTrack);

// 監聽音調變更事件
sender.dtmfSender.ontonechange = function(event) {
    console.log(`當前音調: ${event.tone}`);
};

// 發送 DTMF 音調
sender.dtmfSender.insertDTMF("1");
```

## 解釋
在使用 RTCDTMFToneChangeEvent 時，有幾個常見的注意事項：
- 確保 DTMF 發送者已正確初始化，否則將無法接收到音調變更事件。
- 事件僅在 DTMF 發送者處於活動狀態時觸發，因此請確認發送者對應的媒體流是可用的。
- 部分瀏覽器對 WebRTC 的支持情況可能不同，開發時應注意兼容性問題。

## 總結
RTCDTMFToneChangeEvent 是一個重要的事件，能夠有效地處理 DTMF 音調的變更，並在 WebRTC 應用中提供更好的用戶互動體驗。