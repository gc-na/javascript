<!--
Meta Description: # RTCIceCandidate: JavaScript 中的網絡候選者物件 ## 概要 `RTCIceCandidate` 是一個在 WebRTC 中使用的接口，代表一個 ICE 候選者，這對於建立 P2P（點對點）連接至關重要。 ## 文檔 `RTCIceCandidate` 物件的主要目的是...
Meta Keywords: rtcicecandidate, candidate, ice, rtcpeerconnection, webrtc
-->

# RTCIceCandidate: JavaScript 中的網絡候選者物件

## 概要
`RTCIceCandidate` 是一個在 WebRTC 中使用的接口，代表一個 ICE 候選者，這對於建立 P2P（點對點）連接至關重要。

## 文檔
`RTCIceCandidate` 物件的主要目的是交換網絡信息，以便在 WebRTC 連接中找到最佳的路徑。這些候選者可以是來自不同網絡的 IP 地址，並通過 STUN 或 TURN 伺服器進行獲取。使用 `RTCIceCandidate` 可以有效地協助用戶端在不同的網絡環境下進行實時通信。

### 使用方法
在使用 `RTCIceCandidate` 之前，您需要首先建立一個 `RTCPeerConnection` 物件。然後，您可以使用 `RTCIceCandidate` 對象來傳遞候選者信息。以下是基本的使用流程：

1. 創建一個 `RTCPeerConnection` 實例。
2. 當接收到 ICE 候選者時，使用 `RTCIceCandidate` 來創建候選者。
3. 使用 `addIceCandidate()` 方法將候選者加入到 Peer Connection 中。

### 屬性
- `candidate`: 一個字符串，代表此候選者的描述信息。
- `sdpMid`: 一個可選屬性，表示此候選者所屬的媒體流。
- `sdpMLineIndex`: 一個可選屬性，表示候選者在 SDP 中的行索引。

## 示例
以下是如何使用 `RTCIceCandidate` 的基本示例：

```javascript
// 創建 RTCPeerConnection 實例
const peerConnection = new RTCPeerConnection();

// 當接收到 ICE 候選者時
peerConnection.onicecandidate = (event) => {
    if (event.candidate) {
        // 創建 RTCIceCandidate 實例
        const candidate = new RTCIceCandidate(event.candidate);
        
        // 將候選者加入到 Peer Connection
        peerConnection.addIceCandidate(candidate)
            .then(() => {
                console.log('成功加入候選者');
            })
            .catch((error) => {
                console.error('加入候選者失敗:', error);
            });
    }
};
```

## 解釋
在使用 `RTCIceCandidate` 時，開發者需要注意以下幾點：

- 確保在建立連接之前不會嘗試添加候選者，否則會導致錯誤。
- `addIceCandidate` 方法返回一個 Promise，因此應當使用 `.then()` 和 `.catch()` 來處理成功和失敗的情況。
- 有些環境可能不支持某些 ICE 候選者類型，這可能會導致連接失敗。

## 一句總結
`RTCIceCandidate` 是 WebRTC 中一個關鍵的物件，幫助實現 P2P 連接的網絡候選者管理。