<!--
Meta Description: # RTCPeerConnectionIceEvent：JavaScript 中的 ICE 事件 ## 概述 `RTCPeerConnectionIceEvent` 是一個與 WebRTC 相關的事件，當 ICE（Interactive Connectivity Establishment）候選者被...
Meta Keywords: ice, rtcpeerconnectioniceevent, rtcpeerconnection, 候選者的變化, candidate
-->

# RTCPeerConnectionIceEvent：JavaScript 中的 ICE 事件

## 概述
`RTCPeerConnectionIceEvent` 是一個與 WebRTC 相關的事件，當 ICE（Interactive Connectivity Establishment）候選者被添加或更新時觸發。這個事件對於建立點對點連接非常重要，因為它負責處理網路連接的變化。

## 文檔
### 目的
`RTCPeerConnectionIceEvent` 主要用於監聽 ICE 候選者的變化，這些候選者是用於在不同的網路環境中建立有效的連接的。當 ICE 候選者被發現或更新時，可以使用這個事件來獲取相關信息並進行相應的處理。

### 使用方式
`RTCPeerConnectionIceEvent` 通常與 `RTCPeerConnection` 物件一起使用。開發者可以透過設定事件監聽器來監控 ICE 候選者的變化。以下是基礎的用法說明：

1. 創建一個 `RTCPeerConnection` 實例。
2. 使用 `onicecandidate` 事件來監聽 ICE 候選者的變化。
3. 在事件處理函數中，使用 `RTCPeerConnectionIceEvent` 獲取候選者信息。

### 詳細信息
- **屬性**：
  - `candidate`: 一個 `RTCIceCandidate` 物件，表示新發現的 ICE 候選者。
  
- **事件**：
  - `icecandidate`: 當新候選者被添加時觸發。

## 範例
以下是監聽 `RTCPeerConnectionIceEvent` 的基本範例：

```javascript
// 創建 RTCPeerConnection 實例
const peerConnection = new RTCPeerConnection();

// 設定 ICE 候選者事件的監聽器
peerConnection.onicecandidate = function(event) {
    if (event.candidate) {
        console.log("新候選者:", event.candidate);
    } else {
        console.log("所有候選者已被發現");
    }
};

// 開始連接過程（這裡省略了其他必要的步驟）
```

## 解釋
- **常見的陷阱**：
  - 忘記檢查 `event.candidate` 是否為 `null`，這會導致錯誤的處理邏輯。
  - 在非主線程或非活動上下文中使用 `RTCPeerConnection` 可能會導致事件無法被正確觸發。

- **注意事項**：
  - 確保在 ICE 候選者事件處理函數中執行必要的邏輯，例如向伺服器發送候選者信息，以便進行連接。

## 一行總結
`RTCPeerConnectionIceEvent` 是一個重要的 WebRTC 事件，用於處理 ICE 候選者的變化，幫助開發者建立穩定的點對點連接。