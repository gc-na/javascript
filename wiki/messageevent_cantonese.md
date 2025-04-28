<!--
Meta Description: # JavaScript MessageEvent 事件：全面指南 ## 簡介 MessageEvent 是一個用於處理 Web 應用程式中消息傳遞的 JavaScript 事件。它主要用於 Web Workers 和跨源通信，允許不同的執行上下文之間進行數據傳遞。 ## 文檔 ### 目的 Mes...
Meta Keywords: event, messageevent, javascript, iframe, message
-->

# JavaScript MessageEvent 事件：全面指南

## 簡介
MessageEvent 是一個用於處理 Web 應用程式中消息傳遞的 JavaScript 事件。它主要用於 Web Workers 和跨源通信，允許不同的執行上下文之間進行數據傳遞。

## 文檔
### 目的
MessageEvent 事件的主要目的是在不同執行環境之間傳遞信息，例如主執行線程與 Web Worker 之間，或是不同的 iframe 之間。當一個執行上下文發送消息時，另一個執行上下文將收到一個 MessageEvent 事件，這樣開發者就可以在事件處理器中獲取到這些消息。

### 使用方法
要使用 MessageEvent，開發者需要：
1. 設置一個消息事件的監聽器。
2. 發送消息到另一個執行上下文。
3. 在事件處理器中處理收到的消息。

以下是 MessageEvent 的基本結構：
```javascript
// 設置事件監聽器
window.addEventListener('message', function(event) {
    // 處理接收到的消息
    console.log('Received message:', event.data);
});

// 發送消息
window.postMessage('Hello, World!', '*');
```

### 詳細信息
- **事件屬性**：
  - `data`：包含接收到的數據。
  - `origin`：發送消息的源 URI。
  - `source`：發送消息的窗口對象。
  
- **安全性**：
  - 使用 `postMessage` 時，最好指定目標源，避免安全風險。
  - 在處理接收到的消息時，應確認消息的 `origin` 屬性，確保消息來自可信來源。

## 範例
### 基本使用範例
```javascript
// 主執行線程
window.addEventListener('message', function(event) {
    if (event.origin === 'https://trusted-source.com') {
        console.log('Received:', event.data);
    }
});

// Web Worker
self.onmessage = function(event) {
    self.postMessage('Response from Worker: ' + event.data);
};
```

### 跨源消息傳遞
```javascript
// 在 iframe 中接收消息
window.addEventListener('message', function(event) {
    console.log('Message from parent:', event.data);
});

// 在父頁面中發送消息到 iframe
let iframe = document.getElementById('myIframe');
iframe.contentWindow.postMessage('Hello from parent!', 'https://trusted-iframe-source.com');
```

## 說明
- **常見陷阱**：
  - 忽視 `origin` 檢查會導致安全漏洞，應始終驗證發送方的來源。
  - 使用 `'*'` 作為目標源會使系統暴露於潛在的攻擊。
  
- **注意事項**：
  - 在同一個頁面中，如果多個上下文發送消息，須小心管理事件監聽器，防止混淆消息。
  - `MessageEvent` 只能在支持的瀏覽器中使用，確保檢查兼容性。

## 一句總結
MessageEvent 是一個強大的工具，用於在不同 JavaScript 執行上下文之間安全地傳遞消息。