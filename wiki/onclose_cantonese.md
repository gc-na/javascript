<!--
Meta Description: # JavaScript 的 onclose 事件：完整指南 ## 簡介 `onclose` 是一個 JavaScript 事件，主要用於處理 WebSocket 連接關閉的情況。它允許開發者在連接關閉時執行特定的操作，從而改善用戶體驗和應用程序的穩定性。 ## 文檔 ### 目的 `onclose...
Meta Keywords: onclose, websocket, socket, javascript, code
-->

# JavaScript 的 onclose 事件：完整指南

## 簡介
`onclose` 是一個 JavaScript 事件，主要用於處理 WebSocket 連接關閉的情況。它允許開發者在連接關閉時執行特定的操作，從而改善用戶體驗和應用程序的穩定性。

## 文檔
### 目的
`onclose` 事件的主要目的是監聽 WebSocket 連接何時關閉，並提供一個機會來處理這一事件，例如重新連接或顯示錯誤信息。

### 用法
`onclose` 事件通常與 WebSocket 對象一起使用。當 WebSocket 連接關閉時，將觸發該事件，並可以通過設置 `onclose` 屬性來指定事件處理函數。

### 詳細信息
- **屬性**: `WebSocket.onclose`
- **事件對象**: 當事件被觸發時，事件對象會包含以下屬性：
  - `code`: 關閉的狀態碼，表示為何連接關閉。
  - `reason`: 一個可選的字符串，提供關閉的原因。
  - `wasClean`: 一個布爾值，指示關閉是否是乾淨的。

## 示例
### 基本用法
以下是使用 `onclose` 事件的基本示例：

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onclose = function(event) {
    console.log('WebSocket connection closed:');
    console.log('Code:', event.code);
    console.log('Reason:', event.reason);
    console.log('Was clean:', event.wasClean);
};
```

### 嘗試重新連接
在連接關閉時自動重新連接的示例：

```javascript
function connect() {
    const socket = new WebSocket('ws://example.com/socket');

    socket.onclose = function(event) {
        console.log('Connection closed. Attempting to reconnect...');
        setTimeout(connect, 1000); // 1秒後重新連接
    };
}

connect();
```

## 解釋
### 常見問題
- **如果沒有設置 `onclose` 事件處理器會怎樣？**
  如果不設置，則不會有任何行為響應連接關閉事件，開發者無法得知連接何時關閉。

- **`code` 和 `reason` 的含義是什麼？**
  `code` 是一個數字，表示關閉的狀態碼，通常由 WebSocket 協議定義。`reason` 是一個可選的字符串，提供關閉的具體原因。

### 注意事項
- 確保處理好 `onclose` 事件，特別是在需要保持持久連接的應用中，如即時聊天或實時數據更新的應用。
- 在處理重新連接時，考慮避免無限制的重試，可能會導致過多的請求。

## 一行總結
`onclose` 事件在 JavaScript 中用於監聽 WebSocket 連接的關閉，並允許開發者執行相應的處理邏輯。