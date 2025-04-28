<!--
Meta Description: # PromiseRejectionEvent：JavaScript 中的 Promise 拒絕事件 ## 概述 `PromiseRejectionEvent` 是一個用於處理 JavaScript 中 Promise 拒絕的事件。當一個 Promise 被拒絕且沒有相關的拒絕處理函式時，會觸發此事...
Meta Keywords: promise, promiserejectionevent, javascript, unhandledrejection, event
-->

# PromiseRejectionEvent：JavaScript 中的 Promise 拒絕事件

## 概述
`PromiseRejectionEvent` 是一個用於處理 JavaScript 中 Promise 拒絕的事件。當一個 Promise 被拒絕且沒有相關的拒絕處理函式時，會觸發此事件，讓開發者能夠捕獲和處理未處理的拒絕事件。

## 文件說明
`PromiseRejectionEvent` 提供了一個事件對象，該對象包含了有關未處理的 Promise 拒絕的信息。這個事件可以通過 `window` 對象上的 `unhandledrejection` 事件來監聽。當 Promise 拒絕且未被捕獲時，這個事件會被觸發，方便開發者進行錯誤處理或日誌記錄。

### 目的
`PromiseRejectionEvent` 的主要目的是提高 JavaScript 應用程序的健壯性，幫助開發者識別和處理未捕獲的 Promise 拒絕，以避免潛在的錯誤。

### 用法
要使用 `PromiseRejectionEvent`，可以在全局範圍內註冊 `unhandledrejection` 事件監聽器。

```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('未處理的 Promise 拒絕:', event.reason);
});
```

## 示例
以下是使用 `PromiseRejectionEvent` 的基本示例。

### 示例 1：捕獲未處理的拒絕
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('未處理的拒絕:', event.reason);
});

// 創建一個未被捕獲的 Promise 拒絕
new Promise((resolve, reject) => {
    reject('這是一個拒絕的原因');
});
```

### 示例 2：處理 Promise 拒絕
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('捕獲到未處理的拒絕:', event.reason);
});

// 正確處理 Promise 拒絕
new Promise((resolve, reject) => {
    reject('這是一個拒絕的原因');
}).catch(error => {
    console.log('已處理拒絕:', error);
});
```

## 解釋
在使用 `PromiseRejectionEvent` 時，開發者應注意以下幾點：

1. **未處理拒絕的影響**：如果 Promise 拒絕後未被捕獲，將會觸發 `unhandledrejection` 事件。這可能導致應用程序的行為不如預期，並可能影響用戶體驗。

2. **事件對象**：`PromiseRejectionEvent` 事件對象包含一個 `reason` 屬性，該屬性包含拒絕的原因。開發者應查看這個屬性以獲取錯誤信息。

3. **錯誤處理**：使用 `Promise` 時，建議始終鏈接 `.catch()` 方法來處理拒絕，以防止未處理的拒絕事件。

## 總結
`PromiseRejectionEvent` 是一個強大的工具，幫助開發者捕獲和處理未處理的 Promise 拒絕，從而提升 JavaScript 應用的穩定性和可維護性。