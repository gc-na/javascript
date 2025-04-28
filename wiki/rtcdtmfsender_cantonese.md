<!--
Meta Description: # RTCDTMFSender：JavaScript 中的 DTMF 信號發送器 ## 簡介 RTCDTMFSender 是 WebRTC API 的一部分，允許開發者在實時通信中發送 DTMF（Dual-tone multi-frequency）信號。這對於在語音通話中傳送按鍵操作（如電話導航）非...
Meta Keywords: dtmf, rtcdtmfsender, rtcpeerconnection, createdtmfsender, javascript
-->

# RTCDTMFSender：JavaScript 中的 DTMF 信號發送器

## 簡介
RTCDTMFSender 是 WebRTC API 的一部分，允許開發者在實時通信中發送 DTMF（Dual-tone multi-frequency）信號。這對於在語音通話中傳送按鍵操作（如電話導航）非常有用。

## 文檔
### 目的
RTCDTMFSender 提供了一個接口來發送 DTMF 音調，通常用於 VoIP 應用或其他需要用音頻信號傳遞指令的場景。

### 使用方法
要使用 RTCDTMFSender，您首先需要有一個 RTCPeerConnection 物件。當您創建一個 RTCPeerConnection 並建立通話後，可以通過 `createDTMFSender()` 方法創建一個 DTMF 發送器。

### 詳細信息
- **構造函數**: RTCDTMFSender 沒有公開的構造函數，必須通過 `RTCPeerConnection.createDTMFSender()` 來創建。
- **方法**:
  - `insertDTMF(tones, duration, interToneGap)`: 發送 DTMF 音調，`tones` 參數是一個字符串，包含要發送的 DTMF 音調；`duration` 表示每個音調持續的時間（毫秒）；`interToneGap` 表示音調之間的間隔（毫秒）。
  
- **屬性**:
  - `tracks`: 返回與此 DTMF 發送器關聯的媒體傳輸流（MediaStreamTrack）。

## 範例
```javascript
// 創建 RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 創建 DTMF 發送器
const dtmfSender = peerConnection.createDTMFSender();

// 發送 DTMF 音調
dtmfSender.insertDTMF("123", 100, 50);
```

## 解釋
在使用 RTCDTMFSender 時，有幾個常見的陷阱需要注意：
- 確保在發送 DTMF 音調之前，RTCPeerConnection 已經處於連接狀態。
- DTMF 音調的字符串應該只包含有效的 DTMF 音調字符（0-9, A-D, #, *）。
- 如果您嘗試發送的音調包含無效字符，將不會發送任何音調，且可能會引發錯誤。

## 一句總結
RTCDTMFSender 是一個專門用於在 WebRTC 通信中發送 DTMF 信號的接口，方便實時通話中的按鍵操作。