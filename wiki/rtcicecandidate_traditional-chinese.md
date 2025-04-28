<!--
Meta Description: # RTCIceCandidate：JavaScript 中的實時通訊候選者 ## 摘要 RTCIceCandidate 是 WebRTC API 中的重要組件，用於表示網路連接的候選者，用於建立點對點的媒體連接。它在實時通訊應用程式中扮演著關鍵角色，幫助管理和優化連接的建立過程。 ## 文件說明 ...
Meta Keywords: rtcicecandidate, candidate, javascript, webrtc, nat
-->

# RTCIceCandidate：JavaScript 中的實時通訊候選者

## 摘要
RTCIceCandidate 是 WebRTC API 中的重要組件，用於表示網路連接的候選者，用於建立點對點的媒體連接。它在實時通訊應用程式中扮演著關鍵角色，幫助管理和優化連接的建立過程。

## 文件說明
RTCIceCandidate 是一個包含有關網路候選者的資訊的物件，這些候選者通常是來自 STUN 或 TURN 伺服器的 IP 地址和埠號。這些候選者用於 WebRTC 的 ICE (Interactive Connectivity Establishment) 協議，幫助在 NAT（網路地址轉換）和防火牆後建立直接的媒體流。

### 目的
RTCIceCandidate 的主要目的是提供一個結構化的方式來描述可能用於建立連接的網路路徑。它允許應用程式在不同的網路環境中自動選擇最佳的路徑進行數據傳輸。

### 使用方法
在 JavaScript 中，RTCIceCandidate 通常與 RTCPeerConnection 物件一起使用。當建立 WebRTC 連接時，應用程式會收集候選者並將其傳遞給對等方。

#### 建立 RTCIceCandidate
```javascript
const candidate = new RTCIceCandidate({
  candidate: 'candidate:842163049 1 udp 1677729535 192.0.2.1 12345 typ host',
  sdpMid: 'audio',
  sdpMLineIndex: 0
});
```

## 範例
以下是如何使用 RTCIceCandidate 的基本範例：

### 收集候選者並添加到對等連接
```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.onicecandidate = (event) => {
  if (event.candidate) {
    console.log('新候選者:', event.candidate);
    // 將候選者發送到對方
  }
};

// 假設在某處收到了遠端候選者
const remoteCandidate = new RTCIceCandidate(remoteCandidateData);
peerConnection.addIceCandidate(remoteCandidate)
  .then(() => {
    console.log('成功添加遠端候選者');
  })
  .catch((error) => {
    console.error('添加候選者時發生錯誤:', error);
  });
```

## 解釋
在使用 RTCIceCandidate 時，開發者需要注意以下幾點：

1. **候選者格式**：確保候選者的字符串格式正確，並包含所有必要的屬性。
2. **NAT 和防火牆**：在面對 NAT 或防火牆時，可能需要使用 STUN 或 TURN 伺服器來獲取正確的候選者。
3. **ICE 連接狀態**：隨著候選者的添加，連接狀態可能會改變，開發者應該監控 `iceConnectionState` 以確保連接的穩定性。

## 一句總結
RTCIceCandidate 是 WebRTC 中的核心組件，幫助應用程式在複雜的網路環境中建立穩定的點對點連接。