<!--
Meta Description: # RTCDataChannel：JavaScript 中的實時數據通道 ## 簡介 RTCDataChannel 是 WebRTC（網頁實時通信）技術的一部分，允許在瀏覽器之間建立點對點的數據傳輸通道。這使得開發者能夠在不經過中介伺服器的情況下，直接傳輸文件、消息和其他數據。 ## 文件說明 ##...
Meta Keywords: rtcdatachannel, rtcpeerconnection, datachannel, data, javascript
-->

# RTCDataChannel：JavaScript 中的實時數據通道

## 簡介
RTCDataChannel 是 WebRTC（網頁實時通信）技術的一部分，允許在瀏覽器之間建立點對點的數據傳輸通道。這使得開發者能夠在不經過中介伺服器的情況下，直接傳輸文件、消息和其他數據。

## 文件說明
### 目的
RTCDataChannel 主要用於支持即時數據流的應用程序，例如視頻聊天、遊戲和實時協作工具。它支持低延遲的數據傳輸，並提供可靠性和順序的選項。

### 使用方法
要使用 RTCDataChannel，你需要首先創建一個 RTCPeerConnection 對象，然後使用 `createDataChannel` 方法來創建數據通道。下面是一個基本的使用流程：

1. 建立 RTCPeerConnection 對象。
2. 使用 `createDataChannel` 方法創建一個 RTCDataChannel。
3. 設置事件監聽器以處理數據的接收和通道的狀態變化。
4. 傳輸數據。

### 詳細信息
- **屬性**：
  - `label`: 通道的標籤，識別不同的數據通道。
  - `ordered`: 是否保證數據的順序（默認為 true）。
  - `maxRetransmits`: 最大重傳次數，設置為 0 時表示不進行重傳。
  - `protocol`: 使用的協議名稱（如 "text/plain" 或 "application/octet-stream"）。

- **方法**：
  - `send(data)`: 發送數據到對方。
  - `close()`: 關閉數據通道。

## 示例
以下是使用 RTCDataChannel 的基本示例：

```javascript
// 創建 RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 創建 RTCDataChannel
const dataChannel = peerConnection.createDataChannel("myDataChannel");

// 設置事件監聽器
dataChannel.onopen = () => {
    console.log("Data channel is open!");
    dataChannel.send("Hello, World!");
};

dataChannel.onmessage = (event) => {
    console.log("Received message:", event.data);
};

// 關閉數據通道
dataChannel.onclose = () => {
    console.log("Data channel closed.");
};
```

## 解釋
### 常見問題
- **數據丟失**：若設置 `ordered` 為 false，可能會導致數據接收順序不一致。
- **連接問題**：確保在建立連接之前，兩端的 RTCPeerConnection 已正確配置。
- **瀏覽器兼容性**：不同瀏覽器對 WebRTC 的支持程度不同，請檢查兼容性列表。

### 附註
- 使用 RTCDataChannel 進行大文件傳輸時，建議進行分段和重傳機制的實現。
- 在移動網絡環境中，應注意延遲和丟包情況。

## 一句話總結
RTCDataChannel 使 JavaScript 開發者能夠在瀏覽器之間建立高效的點對點數據傳輸通道。