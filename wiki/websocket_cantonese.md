<!--
Meta Description: # WebSocket 在 JavaScript 中的應用 ## 概述 WebSocket 是一種基於 TCP 的通訊協議，允許在客戶端和伺服器之間進行雙向實時通信。它使得網頁應用程式能夠在不需要不斷輪詢伺服器的情況下獲取數據，從而提高了應用的效能和用戶體驗。 ## 文檔 ### 目的 WebSoc...
Meta Keywords: websocket, socket, javascript, event, function
-->

# WebSocket 在 JavaScript 中的應用

## 概述
WebSocket 是一種基於 TCP 的通訊協議，允許在客戶端和伺服器之間進行雙向實時通信。它使得網頁應用程式能夠在不需要不斷輪詢伺服器的情況下獲取數據，從而提高了應用的效能和用戶體驗。

## 文檔

### 目的
WebSocket 的主要目的是實現持久的連接，使得數據可以在客戶端和伺服器之間即時傳輸，適合用於需要即時更新的應用，如聊天應用、遊戲或實時數據儀表板。

### 使用方法
在 JavaScript 中，使用 WebSocket 非常簡單。你可以通過以下步驟來建立 WebSocket 連接：

1. **創建 WebSocket 實例**：
   ```javascript
   const socket = new WebSocket('ws://yourserver.com/socket');
   ```

2. **監聽事件**：
   - `onopen`：當連接成功時觸發。
   - `onmessage`：當接收到消息時觸發。
   - `onerror`：當發生錯誤時觸發。
   - `onclose`：當連接關閉時觸發。

3. **發送消息**：
   ```javascript
   socket.send('Hello, Server!');
   ```

### 詳細資訊
WebSocket 提供了一個 API 來進行連接和數據傳輸。WebSocket 的連接過程需要進行握手，這通常由瀏覽器自動處理。一次 WebSocket 連接可以支持多次數據的傳輸，並且不需要重新建立連接。

### 事件示範：
以下是一個完整的 WebSocket 使用範例：

```javascript
const socket = new WebSocket('ws://yourserver.com/socket');

// 當連接成功時
socket.onopen = function(event) {
    console.log('WebSocket 連接已開啟');
    socket.send('Hello, Server!');
};

// 當接收到消息時
socket.onmessage = function(event) {
    console.log('從伺服器收到消息：', event.data);
};

// 當發生錯誤時
socket.onerror = function(error) {
    console.log('WebSocket 發生錯誤：', error);
};

// 當連接關閉時
socket.onclose = function(event) {
    console.log('WebSocket 連接已關閉', event);
};
```

## 解釋
使用 WebSocket 時，開發者需注意以下幾點：

1. **連接管理**：確保在不再需要時關閉連接，避免浪費資源。
2. **錯誤處理**：妥善處理 `onerror` 事件，並考慮重試邏輯。
3. **訊息格式**：根據需求選擇適合的數據格式（如 JSON），確保客戶端和伺服器能夠正確解析。

## 總結
WebSocket 是一種高效的通訊協議，能夠在 JavaScript 中實現實時的雙向數據傳輸，適合於各種需要即時更新的應用。