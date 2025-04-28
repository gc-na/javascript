<!--
Meta Description: # RTCSctpTransport：JavaScript 中的 SCTP 傳輸層 ## 概述 RTCSctpTransport 是 WebRTC API 的一部分，專門用於處理 SCTP（實時傳輸控制協議）連接的傳輸層。它允許在點對點的網絡通信中傳輸資料，特別適合需要高效能和低延遲的應用場景，如視...
Meta Keywords: rtcsctptransport, sctp, rtcpeerconnection, webrtc, maxmessagesize
-->

# RTCSctpTransport：JavaScript 中的 SCTP 傳輸層

## 概述
RTCSctpTransport 是 WebRTC API 的一部分，專門用於處理 SCTP（實時傳輸控制協議）連接的傳輸層。它允許在點對點的網絡通信中傳輸資料，特別適合需要高效能和低延遲的應用場景，如視頻會議和即時消息傳遞。

## 文檔
### 目的
RTCSctpTransport 的主要目的是為了提供一個穩定且高效的資料傳輸通道，利用 SCTP 協議的優勢，支持多流傳輸和資料包順序的管理。

### 使用方法
RTCSctpTransport 通常在建立 WebRTC 連接時自動生成，開發者可以透過 RTCPeerConnection 來訪問和控制此對象。以下是使用 RTCSctpTransport 的基本步驟：

1. 創建一個 RTCPeerConnection 對象。
2. 在建立連接之後，使用 `connection.sctp` 屬性訪問 RTCSctpTransport 對象。
3. 利用 RTCSctpTransport 提供的屬性和方法進行資料的傳輸。

### 詳細說明
- **RTCSctpTransport 屬性**
  - `maxRetransmits`：最大重傳次數，控制無法成功發送的資料包重傳的次數。
  - `maxMessageSize`：允許的最大訊息大小，超過此限制的訊息將無法發送。
  
- **RTCSctpTransport 方法**
  - 目前 RTCSctpTransport 並未提供額外的方法，主要通過 RTCPeerConnection 進行操作。

## 示例
以下是一個簡單的使用範例，展示如何在 WebRTC 中使用 RTCSctpTransport。

```javascript
// 創建一個 RTCPeerConnection 實例
const pc = new RTCPeerConnection({
  sdpSemantics: 'unified-plan',
  iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
});

// 等待連接建立後訪問 SCTP 傳輸層
pc.oniceconnectionstatechange = () => {
  if (pc.iceConnectionState === 'connected') {
    const sctpTransport = pc.sctp;
    console.log('SCTP Transport:', sctpTransport);
    
    // 檢查最大消息大小
    console.log('最大訊息大小:', sctpTransport.maxMessageSize);
  }
};

// 創建並發送數據通道
const dataChannel = pc.createDataChannel('myDataChannel', { ordered: true });
dataChannel.onopen = () => {
  dataChannel.send('Hello, SCTP!');
};
```

## 解釋
在使用 RTCSctpTransport 時，有一些常見的注意事項：

- **不支持的瀏覽器**：並非所有瀏覽器都完全支持 SCTP，因此在開發過程中需確認目標瀏覽器的兼容性。
- **性能考量**：雖然 SCTP 提供了多流功能，但在某些情況下，過多的重傳可能會導致延遲增加，需根據實際需求調整 `maxRetransmits`。
- **訊息大小限制**：發送的訊息必須在 `maxMessageSize` 的範圍內，否則會發送失敗，需注意這一點以避免錯誤。

## 一句話總結
RTCSctpTransport 是 WebRTC 的一部分，專為高效的資料傳輸設計，利用 SCTP 協議實現多流和低延遲的通訊。