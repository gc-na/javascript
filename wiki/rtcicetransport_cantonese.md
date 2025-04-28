<!--
Meta Description: # RTCIceTransport: JavaScript 中的實時通信傳輸 ## 簡介 RTCIceTransport 是 WebRTC API 中的一個組件，專責於管理 ICE（Interactive Connectivity Establishment）傳輸的過程，以確保在網絡環境中進行實時音...
Meta Keywords: rtcicetransport, peerconnection, ice, icetransport, new
-->

# RTCIceTransport: JavaScript 中的實時通信傳輸

## 簡介
RTCIceTransport 是 WebRTC API 中的一個組件，專責於管理 ICE（Interactive Connectivity Establishment）傳輸的過程，以確保在網絡環境中進行實時音頻與視頻通信的可靠性和性能。

## 文檔
RTCIceTransport 的主要目的是處理網絡連接的建立、維護和終止。它使用 ICE 協議來確定最佳路由，並能夠在不同的網絡環境中進行自動調整。

### 主要屬性
- **state**: 返回 RTCIceTransport 的當前狀態，可能的值包括 "new"、"checking"、"connected"、"completed"、"failed" 和 "disconnected"。
- **iceGatheringState**: 返回 ICE 收集的當前狀態，可能的值包括 "new"、"gathering" 和 "complete"。

### 主要方法
- **getLocalCandidates()**: 返回當前的本地候選者列表。
- **getRemoteCandidates()**: 返回遠端候選者列表。

### 使用方法
RTCIceTransport 通常作為 RTCPeerConnection 的一部分使用。開發者可通過 RTCPeerConnection 的 `iceTransport` 屬性訪問 RTCIceTransport 實例。

```javascript
const peerConnection = new RTCPeerConnection();
const iceTransport = peerConnection.iceTransport;
```

## 範例
以下是使用 RTCIceTransport 的基本示例：

```javascript
const peerConnection = new RTCPeerConnection();

// 監聽 ICE 狀態變更
peerConnection.iceTransport.onstatechange = () => {
    console.log("ICE Transport state: ", peerConnection.iceTransport.state);
};

// 創建一個 offer
peerConnection.createOffer().then(offer => {
    return peerConnection.setLocalDescription(offer);
}).catch(error => {
    console.error("Error creating offer: ", error);
});
```

## 解釋
使用 RTCIceTransport 時，開發者應注意以下幾點：

- **狀態變更**: RTCIceTransport 的狀態可能會因不同的網絡情況而變化，開發者應該適時對狀態變更進行監聽和處理。
- **候選者收集**: 技術上，候選者的收集過程可能會影響連接的速度和穩定性，建議對此進行優化。
- **錯誤處理**: 在建立連接過程中，可能會遇到多種錯誤，開發者需確保有適當的錯誤處理機制。

## 一句總結
RTCIceTransport 是 WebRTC 中關鍵的組件，負責管理實時通信的網絡連接。