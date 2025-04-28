<!--
Meta Description: # JavaScript 的 onrejectionhandled 事件 ## 概述 `onrejectionhandled` 是一個與 JavaScript Promise 相關的事件，當一個 Promise 被拒絕（rejected）並且與之關聯的拒絕處理程序被執行時，會觸發此事件。這個事件有助...
Meta Keywords: promise, error, onrejectionhandled, javascript, event
-->

# JavaScript 的 onrejectionhandled 事件

## 概述
`onrejectionhandled` 是一個與 JavaScript Promise 相關的事件，當一個 Promise 被拒絕（rejected）並且與之關聯的拒絕處理程序被執行時，會觸發此事件。這個事件有助於開發者監控 Promise 的拒絕情況，並進行適當的錯誤處理。

## 文檔
### 目的
`onrejectionhandled` 事件主要用於當 Promise 被拒絕且該拒絕已經被處理後，讓開發者能夠捕獲和響應該事件。這可以幫助開發者追蹤未處理的拒絕，並改善應用程序的穩定性和可維護性。

### 使用方法
要使用 `onrejectionhandled` 事件，你需要透過 `window` 物件來監聽該事件。以下是基本的語法：

```javascript
window.onrejectionhandled = function(event) {
    // 處理邏輯
    console.log('Promise rejection handled:', event.reason);
};
```

### 詳細信息
- **事件對象**：當 `onrejectionhandled` 事件被觸發時，事件對象會包含一個 `reason` 屬性，這是拒絕的原因。
- **觸發時機**：此事件在 Promise 的拒絕處理程序被調用之後觸發。這意味著你可以在拒絕處理的上下文中進行額外的錯誤記錄或處理。

## 範例
以下是一些基本的用法示例：

### 示例 1：基本用法
```javascript
window.onrejectionhandled = function(event) {
    console.log('Handled rejection:', event.reason);
};

const promise = new Promise((resolve, reject) => {
    reject('Something went wrong!');
});

promise.catch(error => {
    console.error('Caught error:', error);
});
```

### 示例 2：多個 Promise
```javascript
window.onrejectionhandled = function(event) {
    console.log('Rejection handled:', event.reason);
};

const promise1 = new Promise((resolve, reject) => {
    reject('Error in promise 1');
});

const promise2 = new Promise((resolve, reject) => {
    reject('Error in promise 2');
});

promise1.catch(error => {
    console.error('Caught error in promise 1:', error);
});

promise2.catch(error => {
    console.error('Caught error in promise 2:', error);
});
```

## 解釋
### 常見問題
- **未處理的拒絕**：如果 Promise 被拒絕但未被處理，則不會觸發 `onrejectionhandled` 事件。確保在每個 Promise 上使用 `.catch()` 或 `.then()` 來處理拒絕。
- **事件順序**：`onrejectionhandled` 事件在拒絕處理程序後觸發，這意味著如果你在拒絕處理中拋出異常，則可能無法捕獲該事件。

## 一句總結
`onrejectionhandled` 事件幫助開發者監控和管理 JavaScript Promise 的拒絕狀態。