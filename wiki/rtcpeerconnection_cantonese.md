<!--
Meta Description: # RTCPeerConnection：JavaScript 中的網路實時通訊關鍵組件 ## 簡介 RTCPeerConnection 是 WebRTC（Web Real-Time Communication）API 中的核心組件，允許在用戶瀏覽器之間建立直接的音視頻連線，支持即時音訊和視訊通訊。 ...
Meta Keywords: rtcpeerconnection, peerconnection, offer, const, configuration
-->

# RTCPeerConnection：JavaScript 中的網路實時通訊關鍵組件

## 簡介
RTCPeerConnection 是 WebRTC（Web Real-Time Communication）API 中的核心組件，允許在用戶瀏覽器之間建立直接的音視頻連線，支持即時音訊和視訊通訊。

## 文檔
### 目的
RTCPeerConnection 主要用於建立和管理對等連線，實現點對點的音視頻通訊。它負責處理所有的信令、媒體流的傳輸以及網路狀態的管理。

### 用法
RTCPeerConnection 的基本用法如下：

```javascript
// 創建 RTCPeerConnection 實例
const peerConnection = new RTCPeerConnection(configuration);

// 添加媒體流
peerConnection.addStream(localStream);

// 創建本地描述
peerConnection.createOffer()
    .then(offer => peerConnection.setLocalDescription(offer))
    .then(() => {
        // 傳送 offer 給對方
    });

// 接收遠端描述
peerConnection.setRemoteDescription(remoteDescription);
```

### 詳細說明
- **configuration**: RTCPeerConnection 的構建參數，包含 ICE 伺服器的配置。
- **addStream()**: 用於將本地媒體流添加到連線中。
- **createOffer() 和 setLocalDescription()**: 用來創建並設置本地描述，發起連線。
- **setRemoteDescription()**: 用於設定來自對方的描述，完成連線的建立。

## 範例
以下是一個簡單的 RTCPeerConnection 使用示例：

```javascript
const configuration = {
    iceServers: [
        { urls: 'stun:stun.l.google.com:19302' }
    ]
};

const localStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
const peerConnection = new RTCPeerConnection(configuration);

peerConnection.addStream(localStream);

peerConnection.createOffer()
    .then(offer => {
        return peerConnection.setLocalDescription(offer);
    })
    .then(() => {
        // 假設 sendToPeer 是一個函式，用來發送 offer 給對方
        sendToPeer(peerConnection.localDescription);
    });
```

## 解釋
使用 RTCPeerConnection 時需要注意以下幾點：
- ICE 伺服器的配置對連線的穩定性至關重要，確保在配置中包含有效的 STUN 或 TURN 伺服器。
- 必須處理 ICE 候選者的事件，以便在網路環境變化時能夠重新連接。
- 確保在通話過程中適時釋放資源，例如關閉連線和媒體流。

## 一句總結
RTCPeerConnection 是實現 WebRTC 音視頻通訊的關鍵組件，負責建立和管理點對點連線。