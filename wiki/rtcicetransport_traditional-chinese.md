<!--
Meta Description: # RTCIceTransport：JavaScript中的WebRTC傳輸層 ## 概要 RTCIceTransport是WebRTC API的一部分，負責在瀏覽器之間建立和管理媒體傳輸的ICE（Interactive Connectivity Establishment）協議。它確保數據有效、安...
Meta Keywords: peerconnection, event, icetransport, state, new
-->

# RTCIceTransport：JavaScript中的WebRTC傳輸層

## 概要
RTCIceTransport是WebRTC API的一部分，負責在瀏覽器之間建立和管理媒體傳輸的ICE（Interactive Connectivity Establishment）協議。它確保數據有效、安全地在對等端之間傳輸。

## 文檔
### 目的
RTCIceTransport用於處理WebRTC連接中的網絡傳輸。它支持自動選擇最佳的網絡路徑，並在連接過程中處理ICE候選者的發現與選擇。

### 使用方式
要使用RTCIceTransport，開發者通常需要在創建RTCPeerConnection時進行初始化。RTCIceTransport不直接創建，而是作為RTCPeerConnection的一部分自動生成。

#### 屬性
- **state**: 返回當前ICE傳輸的狀態，例如"new", "checking", "connected", "completed", "failed", "disconnected", "closed"。
- **iceGatheringState**: 表示ICE候選者的收集狀態。

#### 方法
RTCIceTransport本身不提供公共方法，但其狀態變化可以通過監聽事件來獲取。

### 事件
- **icecandidate**: 當新的ICE候選者可用時觸發。
- **iceconnectionstatechange**: 當ICE連接狀態發生變化時觸發。

## 範例
以下是使用RTCIceTransport的基本示例：

```javascript
// 創建RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 監聽ICE候選者的事件
peerConnection.onicecandidate = event => {
    if (event.candidate) {
        console.log("新候選者:", event.candidate);
    }
};

// 取得ICE傳輸的狀態
const iceTransport = peerConnection.iceTransport;
console.log("ICE傳輸狀態:", iceTransport.state);
```

## 解釋
在使用RTCIceTransport時，有幾個常見的陷阱和注意事項：
- **網絡環境影響**: 不同的網絡環境可能會影響ICE候選者的可用性和連接狀態。開發者應測試不同的網絡條件。
- **候選者的優先級**: ICE候選者的優先級可能會影響選擇的路徑，確保理解ICE的優先級規則。
- **事件處理**: 正確處理所有ICE相關事件至關重要，特別是在應用程序中需要提供用戶經驗的情況下。

## 總結
RTCIceTransport是WebRTC中的關鍵組件，負責有效管理媒體傳輸的ICE協議，確保對等端之間的高效連接。