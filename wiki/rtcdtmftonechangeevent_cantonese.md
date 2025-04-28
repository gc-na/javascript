<!--
Meta Description: # RTCDTMFToneChangeEvent：JavaScript 的 DTMF 音調變更事件 ## 摘要 `RTCDTMFToneChangeEvent` 是一個在 WebRTC 中使用的事件，當數字傳輸音調（DTMF）發生變更時觸發，主要用於語音通話應用程式中以處理按鍵音。 ## 文檔 `R...
Meta Keywords: dtmf, rtcdtmftonechangeevent, webrtc, tone, rtcpeerconnection
-->

# RTCDTMFToneChangeEvent：JavaScript 的 DTMF 音調變更事件

## 摘要
`RTCDTMFToneChangeEvent` 是一個在 WebRTC 中使用的事件，當數字傳輸音調（DTMF）發生變更時觸發，主要用於語音通話應用程式中以處理按鍵音。

## 文檔
`RTCDTMFToneChangeEvent` 是一個專門用於 WebRTC 的事件，當遠端用戶發送 DTMF 音調時，會創建此事件。此事件的主要目的是讓開發者能夠捕獲及響應 DTMF 音調的變化，這在語音通話應用中非常重要，例如在撥打電話時輸入選項。

### 目的
- 及時捕獲 DTMF 音調變更。
- 使應用能夠對 DTMF 音調做出反應（例如，更新用戶界面或執行特定操作）。

### 用法
在使用 WebRTC 的應用中，你可以通過監聽 `RTCDTMFToneChangeEvent` 事件來獲取 DTMF 音調的變更。此事件通常與 `RTCPeerConnection` 物件相關聯。

### 詳細說明
- **屬性**：
  - `tone`：一個字符串，表示發送的 DTMF 音調，例如 "0" 到 "9"、"#" 和 "*"。
  
- **事件觸發**：
  - 當用戶通過某種方式（如按鍵盤）發送 DTMF 音調時，`RTCDTMFToneChangeEvent` 事件將被觸發。

## 示例
以下是一個簡單的示例，展示如何監聽 `RTCDTMFToneChangeEvent` 事件：

```javascript
const peerConnection = new RTCPeerConnection();

// 監聽 DTMF 音調變更事件
peerConnection.addEventListener('dtmfToneChange', (event) => {
    console.log(`接收到的 DTMF 音調：${event.tone}`);
});

// 假設有一個方法可以發送 DTMF 音調
function sendDTMF(tone) {
    const dtmfSender = peerConnection.createDTMFSender();
    dtmfSender.insertDTMF(tone);
}
```

## 解釋
在使用 `RTCDTMFToneChangeEvent` 時，開發者需要留意以下幾點：
- 確保已經正確設置了 `RTCPeerConnection` 並且已經與遠端用戶建立了連接。
- `RTCDTMFToneChangeEvent` 只在實際的 DTMF 音調變更時觸發，因此開發者需確保其事件處理程式能夠正確識別和處理音調。
- DTMF 音調的格式必須符合標準，否則可能無法正確捕獲。

## 一句總結
`RTCDTMFToneChangeEvent` 是一個用於捕獲 WebRTC 中 DTMF 音調變更的重要事件，對於語音通話應用的開發至關重要。