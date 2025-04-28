<!--
Meta Description: # RTCRtpReceiver：JavaScript中的媒體接收器詳解 ## 概述 RTCRtpReceiver 是 WebRTC API 中的一部分，負責接收傳入的 RTP（實時傳輸協議）媒體流。它允許開發者在客戶端應用程式中處理音頻和視頻數據流，因而在即時通訊和多媒體應用中具有關鍵作用。 ##...
Meta Keywords: rtcrtpreceiver, const, rtcpeerconnection, javascript, peerconnection
-->

# RTCRtpReceiver：JavaScript中的媒體接收器詳解

## 概述
RTCRtpReceiver 是 WebRTC API 中的一部分，負責接收傳入的 RTP（實時傳輸協議）媒體流。它允許開發者在客戶端應用程式中處理音頻和視頻數據流，因而在即時通訊和多媒體應用中具有關鍵作用。

## 文檔
### 目的
RTCRtpReceiver 主要用於接收來自遠端發送者的媒體流，並將其解碼為可供應用程式使用的格式。這對於建立即時通話、視頻會議和其他需要實時媒體傳輸的應用程序來說是必不可少的。

### 使用方法
RTCRtpReceiver 是 RTCRtpSender 的對應物件，通常在創建 RTCPeerConnection 時自動生成。您可以通過 RTCPeerConnection 的 `getReceivers()` 方法獲取當前的 RTCRtpReceiver 實例。

```javascript
const peerConnection = new RTCPeerConnection();

// 獲取接收器
const receivers = peerConnection.getReceivers();
```

### 詳細說明
RTCRtpReceiver 提供數據流的接收功能，並可透過以下屬性和方法進行操作：

- **track**：返回與此接收器相關聯的 RTCRtpMediaStreamTrack 物件，代表接收到的媒體流。
- **getStats()**：返回有關 RTP 接收器狀態的統計數據，這對於分析和調試非常有用。

```javascript
const receiver = receivers[0];
console.log(receiver.track); // 獲取媒體流
receiver.getStats().then(stats => {
  console.log(stats); // 獲取統計數據
});
```

## 例子
### 基本用法
以下是一個簡單的例子，展示如何使用 RTCRtpReceiver 接收媒體流：

```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.ontrack = (event) => {
  const videoElement = document.createElement('video');
  videoElement.srcObject = event.streams[0];
  document.body.appendChild(videoElement);
  videoElement.play();
};

// 假設已經設置了對等連接並發送媒體流
```

## 解釋
### 常見陷阱
1. **未處理的 ontrack 事件**：如果未正確設置 `ontrack` 事件的處理函數，將無法接收媒體流。
2. **不正確的媒體格式**：確保媒體格式與發送端一致，否則可能無法正確解碼。

### 附加說明
RTCRtpReceiver 支持多種媒體類型，並可在不同的瀏覽器中運作。然而，使用者應注意不同瀏覽器之間的兼容性問題，尤其是對於特定的編解碼器支持。

## 總結
RTCRtpReceiver 是一個重要的 WebRTC 組件，允許 JavaScript 應用接收和處理實時音視頻流，以支持即時通訊和多媒體功能。