<!--
Meta Description: # EventSource：JavaScript 中的事件源 API ## 摘要 EventSource 是一個用於接收伺服器發送事件（SSE）的 JavaScript API，能夠實時接收來自伺服器的更新，適用於即時應用。 ## 文檔 ### 目的 EventSource 提供了一種簡單的方法來接...
Meta Keywords: eventsource, event, javascript, console, new
-->

# EventSource：JavaScript 中的事件源 API

## 摘要
EventSource 是一個用於接收伺服器發送事件（SSE）的 JavaScript API，能夠實時接收來自伺服器的更新，適用於即時應用。

## 文檔
### 目的
EventSource 提供了一種簡單的方法來接收伺服器推送的事件，特別適合需要持續接收數據的應用程序，如即時聊天、通知系統和數據流分析。

### 使用方法
要使用 EventSource，您需要創建一個 EventSource 實例，並指定伺服器的端點 URL。這個實例將持續連接伺服器，並在有新事件時觸發相應的事件處理程序。

```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onmessage = function(event) {
    console.log('Received event:', event.data);
};

eventSource.onerror = function(event) {
    console.error('EventSource failed:', event);
};
```

### 詳細說明
- **創建 EventSource 實例**：使用 `new EventSource(url)` 來初始化一個新的實例。
- **事件處理**：
  - `onmessage`：當接收到伺服器推送的事件時觸發，事件對象包含 `data` 屬性，該屬性包含伺服器發送的數據。
  - `onerror`：在發生錯誤或連接中斷時觸發。
- **關閉連接**：可以使用 `eventSource.close()` 方法來關閉與伺服器的連接。

## 示例
### 基本用法
```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onmessage = function(event) {
    console.log('New message from server:', event.data);
};

eventSource.onerror = function(event) {
    console.error('Error occurred:', event);
};

// 關閉連接
setTimeout(() => {
    eventSource.close();
    console.log('EventSource connection closed.');
}, 10000); // 10秒後關閉連接
```

## 解釋
- **常見陷阱**：
  - 確保伺服器端正確配置以支持 SSE。
  - 確保使用的 URL 是正確的，並且伺服器可以持續推送事件。
- **限制**：EventSource 僅支持文本數據，無法接收 JSON 等格式的數據。若需要處理其他數據格式，需在客戶端進行解析。
- **瀏覽器支持**：目前大部分現代瀏覽器均支持 EventSource，但在 IE 及某些舊版瀏覽器中可能不支持。

## 一句話總結
EventSource 是 JavaScript 中一個用於實時接收伺服器推送事件的簡單而有效的 API。