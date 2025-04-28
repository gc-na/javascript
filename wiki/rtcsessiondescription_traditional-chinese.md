<!--
Meta Description: # RTCSessionDescription 在 JavaScript 中的應用與實作 ## 概述 `RTCSessionDescription` 是 WebRTC 介面的一部分，主要用於描述媒體會話的配置和參數。它在建立點對點連接過程中扮演著重要角色，幫助開發者設定音訊、影片流以及其他媒體特性。...
Meta Keywords: rtcsessiondescription, sdp, webrtc, offer, const
-->

# RTCSessionDescription 在 JavaScript 中的應用與實作

## 概述
`RTCSessionDescription` 是 WebRTC 介面的一部分，主要用於描述媒體會話的配置和參數。它在建立點對點連接過程中扮演著重要角色，幫助開發者設定音訊、影片流以及其他媒體特性。

## 文檔
`RTCSessionDescription` 物件包含了會話描述的必要資訊，通常由 SDP（Session Description Protocol）格式的字符串組成。這些描述可用於設置和維護媒體流的連接。

### 目的
`RTCSessionDescription` 用於在 WebRTC 中傳遞媒體流的相關資訊。開發者使用此物件來設定連接的參數，並在建立連接過程中交換會話描述。

### 使用方法
要使用 `RTCSessionDescription`，首先需要創建一個新的實例，然後可以將其傳遞到 `RTCPeerConnection` 的方法中，例如 `setLocalDescription()` 或 `setRemoteDescription()`。

### 屬性
- `type`：會話描述的類型，通常為 `"offer"` 或 `"answer"`。
- `sdp`：一個字符串，包含了會話描述協議的具體內容。

### 建構函數
```javascript
const description = new RTCSessionDescription({
    type: 'offer', // 或 'answer'
    sdp: 'v=0...'
});
```

## 範例
以下是使用 `RTCSessionDescription` 的基本範例：

### 創建和設定本地描述
```javascript
const pc = new RTCPeerConnection();
const offer = await pc.createOffer();
const sessionDescription = new RTCSessionDescription(offer);
await pc.setLocalDescription(sessionDescription);
```

### 設定遠端描述
```javascript
const remoteDescription = new RTCSessionDescription({
    type: 'answer',
    sdp: 'v=0...'
});
await pc.setRemoteDescription(remoteDescription);
```

## 解釋
使用 `RTCSessionDescription` 時，開發者需要注意以下幾點：

1. **SDP 格式**：確保 SDP 字符串的格式正確，否則會導致會話建立失敗。
2. **描述類型**：`type` 屬性必須正確設置為 `"offer"` 或 `"answer"`，這對於 WebRTC 的通訊至關重要。
3. **瀏覽器支持**：檢查所用瀏覽器是否支持 WebRTC 和 `RTCSessionDescription`，因為不同版本的瀏覽器支持程度可能會有所不同。

## 單句總結
`RTCSessionDescription` 是用於描述 WebRTC 媒體會話的物件，對於建立和維護點對點連接至關重要。