<!--
Meta Description: # EventSource 在 JavaScript 中的使用指南 ## 概要 EventSource 是一個 JavaScript 介面，用於從伺服器接收即時更新的事件流，特別適合用於建立單頁應用程式（SPA）和即時通訊應用程式。它支持持久的連接，允許伺服器推送消息到客戶端。 ## 文檔 ### ...
Meta Keywords: eventsource, event, javascript, error, function
-->

# EventSource 在 JavaScript 中的使用指南

## 概要
EventSource 是一個 JavaScript 介面，用於從伺服器接收即時更新的事件流，特別適合用於建立單頁應用程式（SPA）和即時通訊應用程式。它支持持久的連接，允許伺服器推送消息到客戶端。

## 文檔
### 目的
EventSource 的主要目的是提供一個簡單的 API，使開發者能夠從伺服器接收事件流，而無需輪詢。這是一種基於 HTTP 的技術，通常用於實時應用程序，如聊天應用、通知系統等。

### 使用方法
要使用 EventSource，首先需要建立一個新的 EventSource 實例，並提供伺服器端點的 URL。當連接成功後，可以監聽多種事件，例如 `message`、`open` 和 `error`。

#### 基本語法
```javascript
const eventSource = new EventSource(url);
```

### 事件
- **message**: 當接收到新消息時觸發。
- **open**: 當連接成功時觸發。
- **error**: 當發生錯誤或連接關閉時觸發。

## 示例
以下是如何使用 EventSource 接收伺服器推送的消息的簡單示例：

```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onopen = function(event) {
    console.log('連接已開啟');
};

eventSource.onmessage = function(event) {
    console.log('接收到消息:', event.data);
};

eventSource.onerror = function(event) {
    console.error('發生錯誤:', event);
};

// 可以在適當的時候關閉連接
// eventSource.close();
```

在這個示例中，我們連接到伺服器的 `/events` 端點，並使用相應的事件處理程序來處理開啟連接、接收消息和錯誤的情況。

## 解釋
### 常見陷阱
1. **跨域請求**: 若伺服器端不支持 CORS，則可能無法成功建立 EventSource 連接。確保伺服器端正確配置 CORS 標頭。
2. **連接關閉**: 如果連接因為網絡問題或伺服器發生錯誤而關閉，EventSource 將自動嘗試重新連接，但可能需要處理 `error` 事件來確保應用正常運行。
3. **數據格式**: 伺服器發送的數據必須以正確的格式發送，使用 `text/event-stream` MIME 類型。

### 附加說明
EventSource 是一種單向通訊的技術，僅允許伺服器向客戶端推送數據。如果需要雙向通訊，則應考慮 WebSocket。

## 總結
EventSource 是一個強大的 JavaScript API，用於從伺服器實時接收事件流，適合需要即時數據更新的應用程序。