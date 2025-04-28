<!--
Meta Description: # PromiseRejectionEvent：JavaScript 的 Promise 拒絕事件 ## 簡介 `PromiseRejectionEvent` 是 JavaScript 中用於處理 `Promise` 拒絕事件的一種事件。當一個 `Promise` 被拒絕且沒有被處理時，這個事件就會...
Meta Keywords: promise, promiserejectionevent, event, javascript, window
-->

# PromiseRejectionEvent：JavaScript 的 Promise 拒絕事件

## 簡介
`PromiseRejectionEvent` 是 JavaScript 中用於處理 `Promise` 拒絕事件的一種事件。當一個 `Promise` 被拒絕且沒有被處理時，這個事件就會被觸發。這對於捕捉未處理的拒絕和進行錯誤處理非常有用。

## 文檔
### 目的
`PromiseRejectionEvent` 的主要目的是讓開發者能夠監測未處理的 `Promise` 拒絕情況，從而提高應用程序的穩定性和錯誤處理能力。

### 用法
要監聽 `PromiseRejectionEvent`，可以使用 `window.addEventListener` 方法來添加事件監聽器。當一個 `Promise` 被拒絕並且沒有相應的 `.catch()` 處理時，這個事件會被觸發。

#### 語法範例：
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('未處理的拒絕:', event.reason);
});
```

### 詳情
- **event.reason**: 這是 `Promise` 被拒絕時所傳遞的值，通常是錯誤對象或自定義拒絕原因。
- **event.promise**: 這是導致拒絕的 `Promise` 對象。
- 此事件可以幫助開發者追蹤未處理的拒絕並進行調試，以防止應用程序崩潰或行為異常。

## 示例
### 基本用法
以下是一個簡單的示例，展示如何使用 `PromiseRejectionEvent` 來捕獲未處理的拒絕：

```javascript
// 添加事件監聽器
window.addEventListener('unhandledrejection', function(event) {
    console.log('未處理的拒絕:', event.reason);
});

// 創建一個會拒絕的 Promise
const myPromise = new Promise((resolve, reject) => {
    reject(new Error('這是一個錯誤'));
});

// 注意：這個 Promise 沒有 .catch() 處理，事件會被觸發
```

## 解釋
在使用 `Promise` 時，如果沒有為拒絕情況提供處理程序，則會導致未處理的拒絕。這樣的情況可能會影響應用程序的性能和穩定性。開發者應該謹記以下幾點：
- 確保每個 `Promise` 都有適當的 `.catch()` 處理，或者使用 `unhandledrejection` 事件來捕獲未處理的拒絕。
- 對於可能會拒絕的 `Promise`，提前設置錯誤處理能夠提升代碼的健壯性。
- 使用 `PromiseRejectionEvent` 來記錄或追蹤錯誤，以便後續的調試和修復。

## 一句摘要
`PromiseRejectionEvent` 是用於捕獲 JavaScript 中未處理的 `Promise` 拒絕事件的工具，能有效提升錯誤處理能力。