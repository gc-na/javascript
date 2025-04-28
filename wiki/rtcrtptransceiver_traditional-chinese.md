<!--
Meta Description: # RTCRtpTransceiver：JavaScript 中的實時音視頻傳輸控制 ## 概述 RTCRtpTransceiver 是 WebRTC API 中的一個重要組件，主要用於在實時通信中管理音頻和視頻流的傳輸。它支援雙向傳輸，並能夠對音視頻流的發送和接收進行靈活的控制。 ## 文檔 RT...
Meta Keywords: rtcrtptransceiver, transceiver, sender, receiver, const
-->

# RTCRtpTransceiver：JavaScript 中的實時音視頻傳輸控制

## 概述
RTCRtpTransceiver 是 WebRTC API 中的一個重要組件，主要用於在實時通信中管理音頻和視頻流的傳輸。它支援雙向傳輸，並能夠對音視頻流的發送和接收進行靈活的控制。

## 文檔
RTCRtpTransceiver 的主要目的是在 WebRTC 中協調音視頻流的傳遞。它包含兩個主要部分：RTCRtpSender 和 RTCRtpReceiver。RTCRtpTransceiver 使用這兩個部分來處理媒體流的傳輸。

### 主要屬性
- **sender**：返回 RTCRtpSender 對象，負責發送媒體流。
- **receiver**：返回 RTCRtpReceiver 對象，負責接收媒體流。
- **direction**：指示傳輸的方向（如 sendrecv、sendonly、recvonly、inactive）。
- **stopped**：布林值，指示該轉發器是否已停止。

### 主要方法
- **stop()**：停止傳輸並釋放與該轉發器相關的資源。
- **setDirection(direction)**：設置傳輸的方向。

使用 RTCRtpTransceiver 時，通常會在 RTCPeerConnection 的 `addTransceiver` 方法中創建它，並根據需要進行配置。

## 示例
以下是使用 RTCRtpTransceiver 的基本示例：

```javascript
// 創建 RTCPeerConnection 實例
const peerConnection = new RTCPeerConnection();

// 添加音視頻轉發器
const transceiver = peerConnection.addTransceiver('video', { direction: 'sendrecv' });

// 獲取發送器和接收器
const sender = transceiver.sender;
const receiver = transceiver.receiver;

console.log(sender); // 輸出發送器信息
console.log(receiver); // 輸出接收器信息

// 設置傳輸方向
transceiver.setDirection('sendonly');

// 停止轉發器
transceiver.stop();
```

## 解釋
使用 RTCRtpTransceiver 時，開發者需注意以下幾點：

1. **方向設置**：確保在設置傳輸方向時，了解每一個方向的意義，以便能正確控制媒體流的發送和接收。
2. **資源管理**：使用 `stop()` 方法停止轉發器後，記得釋放相關資源，避免內存泄漏。
3. **兼容性**：在某些瀏覽器中，RTCRtpTransceiver 的實現可能存在差異，因此在開發時應進行充分測試。

## 單行摘要
RTCRtpTransceiver 是 WebRTC 中用於靈活控制音視頻流傳輸的關鍵組件。