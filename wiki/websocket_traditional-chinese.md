<!--
Meta Description: # WebSocket：JavaScript中的即時雙向通訊技術 ## 概述 WebSocket 是一種在單個 TCP 連接上進行全雙工通訊的協議，特別適合用於需要即時數據傳輸的應用程式，如即時聊天、遊戲和金融交易。透過 WebSocket，客戶端和伺服器能夠保持持久的連接，實現低延遲的數據交換。 ...
Meta Keywords: websocket, socket, javascript, function, event
-->

# WebSocket：JavaScript中的即時雙向通訊技術

## 概述
WebSocket 是一種在單個 TCP 連接上進行全雙工通訊的協議，特別適合用於需要即時數據傳輸的應用程式，如即時聊天、遊戲和金融交易。透過 WebSocket，客戶端和伺服器能夠保持持久的連接，實現低延遲的數據交換。

## 文檔
### 目的
WebSocket 旨在提供一種高效的途徑，讓客戶端和伺服器之間能夠進行持久的數據交換。與傳統的 HTTP 請求-響應模型相比，WebSocket 可以減少網絡延遲和流量消耗。

### 使用
在 JavaScript 中，WebSocket 由 `WebSocket` 類提供，使用簡單。可以透過以下方式創建一個 WebSocket 連接：

```javascript
const socket = new WebSocket('ws://example.com/socket');
```

### 詳細說明
1. **連接建立**：客戶端發起連接請求，伺服器返回 101 Switching Protocols 響應以建立持久連接。
2. **事件**：
   - `onopen`: 當連接成功建立時觸發。
   - `onmessage`: 當接收到伺服器發送的消息時觸發。
   - `onerror`: 當發生錯誤時觸發。
   - `onclose`: 當連接關閉時觸發。

3. **發送和接收消息**：
   使用 `send()` 方法發送消息，並且透過 `onmessage` 事件接收消息。
   
4. **關閉連接**：
   客戶端可以通過 `close()` 方法主動關閉連接。

## 範例
### 基本使用範例
以下是 WebSocket 的基本使用範例：

```javascript
// 創建 WebSocket 連接
const socket = new WebSocket('ws://example.com/socket');

// 當連接成功建立
socket.onopen = function(event) {
    console.log('WebSocket 連接已建立');
    
    // 發送消息到伺服器
    socket.send('Hello, Server!');
};

// 當接收到伺服器的消息
socket.onmessage = function(event) {
    console.log('接收到消息: ' + event.data);
};

// 當發生錯誤
socket.onerror = function(error) {
    console.error('WebSocket 錯誤: ', error);
};

// 當連接關閉
socket.onclose = function(event) {
    console.log('WebSocket 連接已關閉');
};
```

## 解釋
### 常見問題
- **跨域問題**：WebSocket 通常不會受到同源政策的限制，但伺服器需要正確配置 CORS（跨來源資源共享）以支持來自不同來源的連接。
- **連接不穩定**：由於網絡狀況不佳，WebSocket 連接可能會中斷，需實現重連邏輯以提高穩定性。
- **伺服器支持**：並非所有伺服器都支持 WebSocket，確保所使用的伺服器框架支援 WebSocket。

## 一句總結
WebSocket 是一種高效的即時通訊技術，使 JavaScript 應用程式能夠建立持久的雙向連接。