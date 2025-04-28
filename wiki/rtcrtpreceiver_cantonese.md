<!--
Meta Description: # RTCRtpReceiver 在 JavaScript 中的應用 ## 摘要 RTCRtpReceiver 是 WebRTC API 中的一個重要組件，負責接收 RTP（實時傳輸協議）流並處理音頻或視頻媒體數據。 ## 文檔 ### 目的 RTCRtpReceiver 用於在 WebRTC 應用...
Meta Keywords: rtcrtpreceiver, rtcpeerconnection, track, webrtc, ontrack
-->

# RTCRtpReceiver 在 JavaScript 中的應用

## 摘要
RTCRtpReceiver 是 WebRTC API 中的一個重要組件，負責接收 RTP（實時傳輸協議）流並處理音頻或視頻媒體數據。

## 文檔
### 目的
RTCRtpReceiver 用於在 WebRTC 應用中接收媒體流。它的主要功能是從遠端發送者接收音頻或視頻數據，並將其傳遞給媒體處理流程。此 API 是建立在實時通信基礎上的，旨在為用戶提供低延遲的音視頻傳輸。

### 使用
要使用 RTCRtpReceiver，首先需要創建一個 RTCPeerConnection 實例，然後通過該連接的 `ontrack` 事件來獲取 RTCRtpReceiver 實例。以下是 RTCRtpReceiver 的基本用法：

1. 創建 RTCPeerConnection。
2. 當接收到媒體流時，使用 `ontrack` 事件來獲取 RTCRtpReceiver。

### 詳細資訊
- **屬性**
  - `track`: 獲取與該接收器相關的 MediaStreamTrack。
  - `transport`: 獲取用於傳輸的 RTCDtlsTransport 實例。

- **方法**
  - `getParameters()`: 獲取 RTP 接收器的參數。
  - `getStats()`: 獲取該接收器的統計信息。

## 示例
以下是一個基本的 RTCRtpReceiver 使用示例：

```javascript
// 創建一個新的 RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 當接收到媒體流時
peerConnection.ontrack = (event) => {
    const receiver = event.receiver; // 獲取 RTCRtpReceiver
    const track = event.track; // 獲取 MediaStreamTrack

    console.log(`接收到的媒體類型: ${track.kind}`);
    // 可以進一步處理 track，例如將其添加到一個 video 或 audio 元素中
};

// 假設有一個發送端
const offer = await peerConnection.createOffer();
await peerConnection.setLocalDescription(offer);
```

## 解釋
### 常見陷阱
- 確保已正確設置 `RTCPeerConnection`，以便能夠正確接收媒體流。
- 在處理 `ontrack` 事件時，必須檢查 `event.track` 是否有效。

### 附加說明
- RTCRtpReceiver 只在 WebRTC 環境下運行，因此請確保您在支持 WebRTC 的瀏覽器中測試代碼。
- 通常，RTCRtpReceiver 用於處理來自同一個 RTCPeerConnection 的多個媒體流。

## 一句總結
RTCRtpReceiver 是 WebRTC 中接收音頻和視頻流的核心組件，確保實時通信的流暢性和效率。