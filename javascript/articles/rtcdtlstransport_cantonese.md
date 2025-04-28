<!--
Meta Description: # RTCDtlsTransport：JavaScript 中的 DTLS 傳輸技術 ## Synopsis RTCDtlsTransport 是 WebRTC API 中的一個接口，專門用於實現安全的傳輸層安全性（DTLS）協議，保障音視頻通訊的安全性。 ## Documentation ### ...
Meta Keywords: dtls, rtcdtlstransport, dtlstransport, webrtc, rtcpeerconnection
-->

# RTCDtlsTransport：JavaScript 中的 DTLS 傳輸技術

## Synopsis
RTCDtlsTransport 是 WebRTC API 中的一個接口，專門用於實現安全的傳輸層安全性（DTLS）協議，保障音視頻通訊的安全性。

## Documentation
### 目的
RTCDtlsTransport 主要用於在 WebRTC 應用程式中建立加密的數據通道。它確保在網絡上傳輸的音視頻數據不會被竊聽或篡改。

### 使用方法
RTCDtlsTransport 通常與 RTCPeerConnection 一起使用。當您創建一個 RTCPeerConnection 時，系統會自動生成一個 RTCDtlsTransport 實例，並在需要時進行配置。

### 主要屬性
- **state**: 表示 DTLS 連接的當前狀態，可能的值包括 “new”，“connecting”，“connected”，“closed”，“failed”。
- **onstatechange**: 當 DTLS 傳輸狀態改變時會觸發的事件處理器。

### 主要方法
- **getRemoteCertificates()**: 返回一個包含遠程 DTLS 證書的 Promise。

## Examples
以下是使用 RTCDtlsTransport 的基本示例：

```javascript
const peerConnection = new RTCPeerConnection();

// 獲取 DTLS 傳輸
const dtlsTransport = peerConnection.getSenders()[0].transport;

// 監聽狀態變化
dtlsTransport.onstatechange = () => {
    console.log('DTLS 傳輸狀態:', dtlsTransport.state);
};

// 獲取遠程證書
dtlsTransport.getRemoteCertificates().then(certificates => {
    console.log('遠程證書:', certificates);
});
```

## Explanation
使用 RTCDtlsTransport 時，開發者需要注意以下幾點：
- **狀態管理**: 確保妥善管理 DTLS 傳輸的狀態，以避免在連接失敗後進行不必要的操作。
- **證書管理**: 在獲取和管理證書時，必須理解如何驗證和使用這些證書以確保安全性。
- **錯誤處理**: 要準備好處理可能出現的錯誤，例如證書驗證失敗或連接失敗的情況。

## One Line Summary
RTCDtlsTransport 是 WebRTC 中用於實現安全 DTLS 連接的關鍵接口，確保音視頻傳輸的安全性。