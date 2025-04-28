<!--
Meta Description: # JavaScript postMessage：跨來源通訊的解決方案 ## Synopsis `postMessage` 是一個 JavaScript 方法，允許不同來源（例如，不同域名或不同窗口）之間安全地傳遞信息，主要用於跨來源的網頁應用程序中。 ## Documentation `postM...
Meta Keywords: postmessage, javascript, message, iframe, event
-->

# JavaScript postMessage：跨來源通訊的解決方案

## Synopsis
`postMessage` 是一個 JavaScript 方法，允許不同來源（例如，不同域名或不同窗口）之間安全地傳遞信息，主要用於跨來源的網頁應用程序中。

## Documentation
`postMessage` 方法屬於 `Window` 物件，主要用來在不同的窗口、iframe 或者 web worker 之間傳遞消息。這是一個重要的功能，因為它能夠克服同源政策的限制，促進跨來源的數據交流。

### 語法
```javascript
window.postMessage(message, targetOrigin, [transfer]);
```

### 參數
- **message**: 要傳遞的數據，這可以是任何 JavaScript 物件。
- **targetOrigin**: 接收消息的窗口的來源（域名）。這對安全性至關重要，以確保消息只發送到信任的來源。
- **transfer**: （可選）一個 `Transferable` 物件的陣列，這些物件會被轉移而不是複製。

### 返回值
無，`postMessage` 是一個不返回任何值的函數。

## Examples
### 基本使用範例
以下是一個簡單的例子，展示如何使用 `postMessage` 來發送消息：

**主窗口代碼：**
```javascript
const iframe = document.getElementById('myIframe');
const message = { type: 'greeting', text: '你好，iframe！' };

iframe.contentWindow.postMessage(message, 'https://example.com');
```

**iframe 代碼：**
```javascript
window.addEventListener('message', (event) => {
    if (event.origin === 'https://your-domain.com') {
        console.log('收到消息:', event.data);
    }
});
```

## Explanation
使用 `postMessage` 時需要注意以下幾點：

1. **安全性**: 確保 `targetOrigin` 的正確性，以防止信息泄露給不受信任的來源。
2. **消息格式**: 傳遞的消息可以是物件，但必須是可序列化的，否則會丟失。
3. **事件監聽器**: 在接收方必須設置 `message` 事件的監聽器，以便接收消息。

### 常見陷阱
- 忘記檢查 `event.origin` 會導致安全漏洞，接收不可信的消息。
- 當使用 `Transferable` 物件時，要注意這些物件在傳遞後會失去對原始物件的引用。

## One Line Summary
`postMessage` 是一個用於安全地在不同來源之間傳遞消息的 JavaScript 方法。