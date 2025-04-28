<!--
Meta Description: # RTCSessionDescription：JavaScript 中的實時通訊會話描述 ## 簡介 `RTCSessionDescription` 是 WebRTC API 中的一個重要接口，用於描述媒體會話的基本信息。它包含了會話的配置，如音頻和視頻編碼格式，並且是設置點對點連接時必不可少的一...
Meta Keywords: rtcsessiondescription, sdp, error, offer, webrtc
-->

# RTCSessionDescription：JavaScript 中的實時通訊會話描述

## 簡介
`RTCSessionDescription` 是 WebRTC API 中的一個重要接口，用於描述媒體會話的基本信息。它包含了會話的配置，如音頻和視頻編碼格式，並且是設置點對點連接時必不可少的一部分。

## 文檔
`RTCSessionDescription` 的主要目的是為 WebRTC 提供一個結構化的方式來描述媒體會話的詳細信息。它的構造函數接收一個對象，該對象包括以下屬性：

- **type**：會話類型，通常為 "offer" 或 "answer"。
- **sdp**：會話描述協議 (SDP) 字符串，包含了該會話的媒體信息。

### 用法
要使用 `RTCSessionDescription`，首先需要創建一個新的 `RTCSessionDescription` 實例，然後可以將其用於設置或接收 WebRTC 連接的會話描述。

**範例**：
```javascript
// 創建一個 RTCSessionDescription 實例
const offer = new RTCSessionDescription({
    type: 'offer',
    sdp: 'v=0\r\n...' // 此處填入有效的 SDP 字符串
});

// 使用該描述來設置本地會話
peerConnection.setLocalDescription(offer)
    .then(() => {
        console.log('本地描述已設置');
    })
    .catch(error => {
        console.error('設置本地描述時出錯:', error);
    });
```

## 範例
以下是一個基本的使用範例，展示如何創建和使用 `RTCSessionDescription`：

```javascript
// 創建 RTCSessionDescription
const sessionDescription = new RTCSessionDescription({
    type: 'answer',
    sdp: 'v=0\r\n...' // 用於示例的 SDP 字符串
});

// 設定本地描述
peerConnection.setLocalDescription(sessionDescription)
    .then(() => {
        console.log('成功設置本地描述');
    })
    .catch(error => {
        console.error('設置本地描述失敗:', error);
    });
```

## 解釋
在使用 `RTCSessionDescription` 時，開發者可能會遇到以下常見問題：

1. **SDP 格式錯誤**：如果提供的 SDP 字符串格式不正確，會導致連接失敗。確保使用有效的 SDP 格式。
2. **類型錯誤**：`type` 屬性必須是 "offer" 或 "answer"，否則會報錯。
3. **非同步操作**：`setLocalDescription` 是一個非同步操作，需確保在成功回調中處理後續邏輯。

## 一句總結
`RTCSessionDescription` 是 WebRTC 中用於描述媒體會話的關鍵接口，確保正確使用 SDP 和類型以建立成功的連接。