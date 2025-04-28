<!--
Meta Description: # WebSocketStream：JavaScript 中的實時資料流技術 ## 概述 WebSocketStream 是一種基於 WebSocket 協議的資料流技術，允許在客戶端和伺服器之間進行雙向、持久的實時通訊。它為開發者提供了一種高效能的方式來處理即時數據傳輸，特別適合需要快速更新的應用...
Meta Keywords: websocket, websocketstream, socket, javascript, error
-->

# WebSocketStream：JavaScript 中的實時資料流技術

## 概述
WebSocketStream 是一種基於 WebSocket 協議的資料流技術，允許在客戶端和伺服器之間進行雙向、持久的實時通訊。它為開發者提供了一種高效能的方式來處理即時數據傳輸，特別適合需要快速更新的應用，如聊天應用、即時遊戲和金融交易平台。

## 文檔
### 目的
WebSocketStream 旨在提供一種可靠的通訊方式，通過持久的連接來傳送資料，避免了傳統 HTTP 請求的開銷。這使得即時應用的開發變得更加簡單且高效。

### 使用方式
要使用 WebSocketStream，開發者需要建立一個 WebSocket 連接，然後使用它來發送和接收訊息。以下是其基本的用法：

1. **建立連接**：
   ```javascript
   const webSocketStream = new WebSocket('ws://yourserver.com/socket');
   ```

2. **發送資料**：
   ```javascript
   webSocketStream.send(JSON.stringify({ type: 'message', content: 'Hello, World!' }));
   ```

3. **接收資料**：
   ```javascript
   webSocketStream.onmessage = (event) => {
       const data = JSON.parse(event.data);
       console.log(data);
   };
   ```

4. **錯誤處理**：
   ```javascript
   webSocketStream.onerror = (error) => {
       console.error('WebSocket error:', error);
   };
   ```

### 詳細說明
WebSocketStream 允許開發者在客戶端和伺服器之間建立持久的連接。這種連接在兩邊都可以主動發送訊息，而不需要每次都重新建立連接。這不僅提高了效率，也減少了延遲。

- **連接狀態**：WebSocket 資源有多種狀態：CONNECTING、OPEN、CLOSING 和 CLOSED。開發者可以使用這些狀態來管理連接的生命週期。
- **資料格式**：傳輸的資料格式通常是 JSON，這使得資料解析和處理變得更加方便。
- **安全性**：WebSocket 也支持加密連接（wss://），這對於需要安全性傳輸的應用而言至關重要。

## 範例
### 基本用法範例
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = () => {
    console.log('WebSocket 連接已開啟！');
    socket.send('你好，伺服器！');
};

socket.onmessage = (event) => {
    console.log('來自伺服器的訊息：', event.data);
};

socket.onerror = (error) => {
    console.error('WebSocket 錯誤：', error);
};

socket.onclose = () => {
    console.log('WebSocket 連接已關閉。');
};
```

## 解釋
- **常見問題**：
  - **連接失敗**：確保伺服器正在運行，並且 WebSocket URL 正確。
  - **資料格式**：傳送和接收的資料格式必須一致，否則會導致解析錯誤。
  - **瀏覽器支持**：大多數現代瀏覽器支持 WebSocket，但舊版瀏覽器可能不支持。

- **建議**：
  - 使用 `try-catch` 來捕捉 JSON 解析的錯誤，確保應用的健壯性。
  - 為 WebSocket 連接的事件添加適當的處理函數，以管理不同的連接狀態。

## 一句總結
WebSocketStream 提供了一種高效的方式來實現 JavaScript 中的實時雙向通訊，適合需要快速數據更新的應用。