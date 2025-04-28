<!--
Meta Description: # CloseEvent 在 JavaScript 中的應用與用途 ## 概述 CloseEvent 是一個在 JavaScript 中用於處理 WebSocket 和其他事件的關閉事件的接口。它提供了關閉連接時的相關信息，幫助開發者更好地管理連接狀態。 ## 文檔 ### 目的 CloseEven...
Meta Keywords: closeevent, websocket, event, console, log
-->

# CloseEvent 在 JavaScript 中的應用與用途

## 概述
CloseEvent 是一個在 JavaScript 中用於處理 WebSocket 和其他事件的關閉事件的接口。它提供了關閉連接時的相關信息，幫助開發者更好地管理連接狀態。

## 文檔
### 目的
CloseEvent 用於 WebSocket 連接關閉時的事件處理。當 WebSocket 連接因為各種原因關閉時，會觸發此事件，並提供關閉的狀態碼和原因。

### 使用方法
在使用 CloseEvent 時，通常需要監聽 WebSocket 實例的 `onclose` 事件。當連接關閉時，可以訪問 CloseEvent 的屬性來獲取關閉狀態的詳細信息。

### 詳細信息
CloseEvent 的屬性包括：
- `code`：關閉連接的狀態碼，指示關閉的具體原因。
- `reason`：一個可選的字串，解釋關閉的原因。
- `wasClean`：布爾值，指示關閉是否正常完成。

這些屬性對於調試連接問題和管理用戶體驗非常重要。

## 範例
以下是一個使用 CloseEvent 的基本範例：

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onclose = function(event) {
    console.log('連接已關閉：');
    console.log('狀態碼：', event.code);
    console.log('原因：', event.reason);
    console.log('是否正常關閉：', event.wasClean);
};
```

在這個例子中，當 WebSocket 連接關閉時，會在控制台輸出關閉的狀態碼、原因以及是否正常關閉的情況。

## 解釋
在使用 CloseEvent 時，開發者需要注意以下幾點：
- 確保在使用 WebSocket 之前已正確設置事件監聽器，否則可能會錯過關閉事件。
- 不同的狀態碼可能代表不同的情況。例如，1000 代表正常關閉，而 1006 則表示異常關閉。
- 若未處理 onclose 事件，可能會導致用戶無法獲知連接狀態的變化，影響用戶體驗。

## 一句總結
CloseEvent 是處理 WebSocket 連接關閉時的重要事件，提供關閉狀態的詳細信息，幫助開發者管理連接。