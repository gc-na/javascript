<!--
Meta Description: # RTCPeerConnection - JavaScript中的實時通信核心 ## 概述 RTCPeerConnection是WebRTC API中的一個關鍵組件，用於建立點對點的音頻和視頻通訊。它允許開發者在瀏覽器之間創建直接的網絡連接，以支持即時通訊應用程式。 ## 文檔 ### 目的 RT...
Meta Keywords: peerconnection, configuration, rtcpeerconnection, const, then
-->

# RTCPeerConnection - JavaScript中的實時通信核心

## 概述
RTCPeerConnection是WebRTC API中的一個關鍵組件，用於建立點對點的音頻和視頻通訊。它允許開發者在瀏覽器之間創建直接的網絡連接，以支持即時通訊應用程式。

## 文檔
### 目的
RTCPeerConnection的主要目的是支持高效的音視頻數據傳輸，並提供可靠的網絡連接功能。它負責處理連接的建立、維護以及終止過程。

### 使用方式
要使用RTCPeerConnection，首先需要創建一個新的RTCPeerConnection實例，然後可以添加媒體流、設置ICE候選者並進行信號交換。

#### 語法
```javascript
const peerConnection = new RTCPeerConnection(configuration);
```

#### 參數
- **configuration**: 一個可選的對象，包含ICE伺服器的配置信息，例如：
  - `iceServers`: 一個ICE伺服器的數組，用於網絡地址轉換。

### 主要方法
- `createOffer()`: 創建一個新的SDP描述，表示發起連接的請求。
- `createAnswer()`: 回應對方的請求，創建一個SDP描述。
- `setLocalDescription()`: 設置本地SDP描述。
- `setRemoteDescription()`: 設置遠程SDP描述。
- `addIceCandidate()`: 增加ICE候選者以建立連接。

## 範例
### 基本用法
以下是一個簡單的RTCPeerConnection用法範例，展示如何創建連接並發送視頻流。

```javascript
// 創建RTCPeerConnection實例
const configuration = {
    iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
};
const peerConnection = new RTCPeerConnection(configuration);

// 添加本地媒體流
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

// 創建並發送offer
peerConnection.createOffer().then(offer => {
    return peerConnection.setLocalDescription(offer);
}).then(() => {
    // 通知對方發送offer
});
```

## 解釋
### 常見陷阱與注意事項
- **ICE候選者的處理**: 確保適當地處理ICE候選者的收發，否則可能會導致連接失敗。
- **SDP格式**: 注意SDP描述的格式，因為不正確的格式可能導致無法建立連接。
- **跨域問題**: 在使用WebRTC時，確保你的應用程式具備正確的HTTPS支持，否則某些功能可能無法正常工作。

## 總結
RTCPeerConnection是一個強大的WebRTC API組件，能夠實現高效的點對點音視頻通訊，為即時通訊應用提供支持。