<!--
Meta Description: # RTCRtpTransceiver：JavaScript 中的媒體傳輸組件 ## 概述 RTCRtpTransceiver 是 WebRTC API 中的一個重要組件，負責在多媒體通信中處理音頻和視頻的傳輸。它允許開發者在實時通信應用中靈活地管理媒體流。 ## 文檔 RTCRtpTranscei...
Meta Keywords: rtcrtptransceiver, rtcpeerconnection, const, peerconnection, transceiver
-->

# RTCRtpTransceiver：JavaScript 中的媒體傳輸組件

## 概述
RTCRtpTransceiver 是 WebRTC API 中的一個重要組件，負責在多媒體通信中處理音頻和視頻的傳輸。它允許開發者在實時通信應用中靈活地管理媒體流。

## 文檔
RTCRtpTransceiver 的主要目的是在 WebRTC 中簡化音視頻流的傳輸和控制。這個組件能夠協調音頻和視頻的發送與接收，並且支持媒體流的動態變更。

### 使用方式
RTCRtpTransceiver 通常與 RTCPeerConnection 一起使用。當創建 RTCPeerConnection 時，可以通過呼叫 `addTransceiver` 方法來添加一個新的 RTCRtpTransceiver。

#### 主要屬性
- **sender**：表示媒體發送器的 RTCRtpSender 對象。
- **receiver**：表示媒體接收器的 RTCRtpReceiver 對象。
- **direction**：表示傳輸的方向，可以是 'sendrecv'、'sendonly'、'recvonly' 或 'inactive'。

#### 創建和管理
```javascript
const peerConnection = new RTCPeerConnection();
const transceiver = peerConnection.addTransceiver('video', { direction: 'sendrecv' });
```

## 範例
以下是一個基本的使用範例，展示如何創建 RTCRtpTransceiver 並添加媒體流：

```javascript
// 創建 RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 添加音頻和視頻的 transceiver
const audioTransceiver = peerConnection.addTransceiver('audio', { direction: 'sendrecv' });
const videoTransceiver = peerConnection.addTransceiver('video', { direction: 'sendrecv' });

// 獲取用戶媒體
navigator.mediaDevices.getUserMedia({ audio: true, video: true })
  .then(stream => {
    // 將媒體流添加到 transceiver
    stream.getTracks().forEach(track => {
      if (track.kind === 'audio') {
        audioTransceiver.sender.replaceTrack(track);
      } else if (track.kind === 'video') {
        videoTransceiver.sender.replaceTrack(track);
      }
    });
  })
  .catch(error => {
    console.error('獲取媒體失敗:', error);
  });
```

## 解釋
在使用 RTCRtpTransceiver 時，需要注意以下幾點：
- **方向**：確保正確設置 transceiver 的方向，以免造成媒體流的意外中斷。
- **動態變更**：可以在會話中隨時改變 transceiver 的方向或添加新的媒體流，但需要仔細管理相關的媒體狀態。
- **瀏覽器兼容性**：不同瀏覽器對 WebRTC 的支持程度不同，開發時需做兼容性測試。

## 一句總結
RTCRtpTransceiver 是 WebRTC 中管理媒體傳輸的關鍵組件，幫助開發者實現靈活的音視頻流控制。