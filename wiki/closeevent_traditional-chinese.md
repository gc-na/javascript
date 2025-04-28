<!--
Meta Description: # CloseEvent: JavaScript 中的關閉事件 ## 摘要 `CloseEvent` 是一個在 JavaScript 中用於處理 WebSocket 和其他連接的特定關閉事件的接口。當連接關閉時，該事件會被觸發，並提供有關關閉的詳細資訊。 ## 文檔 ### 目的 `CloseEve...
Meta Keywords: closeevent, websocket, socket, event, code
-->

# CloseEvent: JavaScript 中的關閉事件

## 摘要
`CloseEvent` 是一個在 JavaScript 中用於處理 WebSocket 和其他連接的特定關閉事件的接口。當連接關閉時，該事件會被觸發，並提供有關關閉的詳細資訊。

## 文檔
### 目的
`CloseEvent` 主要用於捕獲和處理連接關閉的事件，尤其是在 WebSocket 應用程式中。當連接因正常或異常原因而關閉時，開發者可以使用此事件來執行相應的操作。

### 使用方法
`CloseEvent` 事件可以在 WebSocket 的 `onclose` 事件處理器中使用。當 WebSocket 連接關閉時，會自動觸發該事件，並可以訪問 `CloseEvent` 對象以獲取狀態碼和關閉的原因。

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onclose = function(event) {
    console.log('WebSocket closed with code:', event.code);
    console.log('Reason:', event.reason);
};
```

### 詳細信息
`CloseEvent` 對象包含以下屬性：
- **code**: 一個數字，表示關閉連接的狀態碼。
- **reason**: 關閉的原因，通常是由伺服器提供的字符串。
- **wasClean**: 一個布林值，表示關閉是否是乾淨的（即沒有錯誤）。

## 範例
以下是 `CloseEvent` 的基本使用範例：

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    console.log('WebSocket connection opened.');
};

socket.onclose = function(event) {
    if (event.wasClean) {
        console.log(`Closed cleanly, code: ${event.code}, reason: ${event.reason}`);
    } else {
        console.error(`Connection died, code: ${event.code}`);
    }
};

// 假設在某個時候關閉連接
socket.close(1000, 'Normal closure');
```

## 解釋
在使用 `CloseEvent` 時，開發者需要注意以下幾點：
- **狀態碼**: 根據 RFC 6455，狀態碼必須是 1000 到 4999 之間的數字。常見的狀態碼包括 1000（正常關閉）、1001（主機關閉）等。
- **關閉原因**: 雖然 `reason` 屬性是可選的，但提供一個清晰的關閉原因對於調試非常有幫助。
- **異常處理**: 在處理 `onclose` 事件時，應考慮到可能的非預期關閉情況，並適當地記錄或提示用戶。

## 總結
`CloseEvent` 是 JavaScript 中一個重要的事件，用於處理 WebSocket 連接的關閉，提供有關關閉原因的詳細資訊，對於維護穩定的應用程式至關重要。