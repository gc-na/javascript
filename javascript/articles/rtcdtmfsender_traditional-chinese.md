<!--
Meta Description: # RTCDTMFSender：JavaScript 中的 DTMF 發送器 ## 概述 RTCDTMFSender 是 WebRTC API 中的一個接口，允許開發者在網路通話中發送 DTMF（雙音多頻）信號。這個功能對於在通話中輸入數字或指令，如呼叫選單，尤其重要。 ## 文件說明 ### 目的...
Meta Keywords: dtmf, rtcdtmfsender, javascript, webrtc, rtcpeerconnection
-->

# RTCDTMFSender：JavaScript 中的 DTMF 發送器

## 概述
RTCDTMFSender 是 WebRTC API 中的一個接口，允許開發者在網路通話中發送 DTMF（雙音多頻）信號。這個功能對於在通話中輸入數字或指令，如呼叫選單，尤其重要。

## 文件說明
### 目的
RTCDTMFSender 的主要目的是在即時通訊應用中提供 DTMF 信號的發送能力，這樣用戶可以在通話期間輸入數字或符號以進行互動。

### 使用方法
要使用 RTCDTMFSender，首先需要建立一個 RTCPeerConnection 實例。然後，可以通過該連接的 `createDTMFSender()` 方法創建一個 RTCDTMFSender 實例。

### 詳細說明
- **創建 DTMF 發送器**: 
  ```javascript
  let peerConnection = new RTCPeerConnection();
  let dtmfSender = peerConnection.createDTMFSender(track);
  ```

- **發送 DTMF 信號**: 
  使用 `insertDTMF()` 方法可以發送 DTMF 信號。
  ```javascript
  dtmfSender.insertDTMF("1234", 0, 100);
  ```
  這裡的 `"1234"` 是要發送的 DTMF 字符串，第二個參數是開始時間（以毫秒為單位），第三個參數是持續時間。

- **屬性**:
  - `track`：關聯的媒體軌道。
  - `onerror`：錯誤回調函數。

## 範例
以下是一個簡單的示範，展示如何在網路通話中發送 DTMF 信號：

```javascript
// 創建一個 RTCPeerConnection 實例
let peerConnection = new RTCPeerConnection();

// 假設 track 是一個有效的媒體軌道
let dtmfSender = peerConnection.createDTMFSender(track);

// 發送 DTMF 信號
dtmfSender.insertDTMF("1234", 0, 100);
```

## 解釋
### 常見陷阱
- **未正確設置媒體軌道**: 確保在創建 DTMF 發送器時傳遞有效的媒體軌道。
- **錯誤的持續時間**: 如果持續時間設置為零，DTMF 信號將不會被發送。
- **支持性**: 並非所有瀏覽器都支持 WebRTC 和 DTMF，因此需要確認目標瀏覽器的兼容性。

### 其他注意事項
- 需要在安全的上下文（HTTPS）中使用 WebRTC。
- RTCDTMFSender 的使用與網路延遲和通話質量有關，因此在高延遲情況下可能會影響 DTMF 信號的接收。

## 總結
RTCDTMFSender 是一個重要的接口，允許在 WebRTC 通話中發送 DTMF 信號，增強了用戶的互動能力。