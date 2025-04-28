<!--
Meta Description: # webkitRTCPeerConnection：JavaScript 中的 WebRTC 連接管理 ## 摘要 `webkitRTCPeerConnection` 是 WebRTC 的一部分，提供了一個用於建立點對點連接的 API。它允許用戶端之間進行音頻、視頻和數據的實時傳輸，廣泛應用於視頻會...
Meta Keywords: peerconnection, webkitrtcpeerconnection, javascript, webrtc, stream
-->

# webkitRTCPeerConnection：JavaScript 中的 WebRTC 連接管理

## 摘要
`webkitRTCPeerConnection` 是 WebRTC 的一部分，提供了一個用於建立點對點連接的 API。它允許用戶端之間進行音頻、視頻和數據的實時傳輸，廣泛應用於視頻會議和即時通訊應用中。

## 文檔
`webkitRTCPeerConnection` 的主要目的是支持 WebRTC 的實時通信功能。這個接口允許開發者創建和管理連接，進行媒體流的傳輸，並處理 ICE（Interactive Connectivity Establishment）候選者。

### 使用方法
要使用 `webkitRTCPeerConnection`，首先需要創建一個實例，並設置必要的配置參數。以下是基本的使用步驟：

1. **創建 PeerConnection 物件**:
   ```javascript
   const configuration = {
       iceServers: [
           { urls: 'stun:stun.l.google.com:19302' }
       ]
   };
   const peerConnection = new webkitRTCPeerConnection(configuration);
   ```

2. **添加媒體流**:
   使用 `addTrack` 或 `addStream` 方法將媒體流添加到連接中。
   ```javascript
   navigator.mediaDevices.getUserMedia({ video: true, audio: true })
       .then(stream => {
           stream.getTracks().forEach(track => {
               peerConnection.addTrack(track, stream);
           });
       });
   ```

3. **創建和發送 offer**:
   使用 `createOffer` 方法創建一個連接請求，然後發送給對端。
   ```javascript
   peerConnection.createOffer()
       .then(offer => {
           return peerConnection.setLocalDescription(offer);
       })
       .then(() => {
           // 發送 offer 到對端
       });
   ```

4. **處理 ICE 候選者**:
   當新的 ICE 候選者生成時，可以通過 `onicecandidate` 事件來處理。
   ```javascript
   peerConnection.onicecandidate = event => {
       if (event.candidate) {
           // 發送 ICE 候選者到對端
       }
   };
   ```

## 範例
以下是一個簡單的 WebRTC 示例，展示了如何使用 `webkitRTCPeerConnection` 進行視頻通話：

```javascript
const peerConnection = new webkitRTCPeerConnection({
    iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
});

navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        const videoElement = document.querySelector('video');
        videoElement.srcObject = stream;
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

peerConnection.onicecandidate = event => {
    if (event.candidate) {
        // 發送 candidate
    }
};

peerConnection.createOffer()
    .then(offer => peerConnection.setLocalDescription(offer))
    .then(() => {
        // 發送 offer
    });
```

## 解釋
在使用 `webkitRTCPeerConnection` 時，開發者需要注意以下幾點：

- **瀏覽器相容性**：`webkitRTCPeerConnection` 是 WebRTC 的早期實現，可能在某些現代瀏覽器中已被標準的 `RTCPeerConnection` 替代。建議檢查當前瀏覽器的支持情況。
- **ICE 候選者**：在建立連接時，ICE 候選者的處理至關重要，確保所有候選者均能正確傳遞給對端。
- **安全性**：WebRTC 應用通常需要在 HTTPS 環境下運行，這是支持安全連接的必要條件。

## 一句話總結
`webkitRTCPeerConnection` 是 JavaScript 中用於實現 WebRTC 即時通訊的關鍵 API，支持音視頻流的點對點傳輸。