<!--
Meta Description: # JavaScript 的 onrejectionhandled 事件詳解 ## 簡介 `onrejectionhandled` 是一個用於處理 Promise 拒絕狀態的事件，當一個拒絕的 Promise 被處理時，會觸發這個事件。此事件可以幫助開發者追蹤和管理 Promise 的錯誤處理過程。...
Meta Keywords: onrejectionhandled, promise, event, javascript, console
-->

# JavaScript 的 onrejectionhandled 事件詳解

## 簡介
`onrejectionhandled` 是一個用於處理 Promise 拒絕狀態的事件，當一個拒絕的 Promise 被處理時，會觸發這個事件。此事件可以幫助開發者追蹤和管理 Promise 的錯誤處理過程。

## 文檔
`onrejectionhandled` 事件是 JavaScript 中的一個全局事件，主要目的是在 Promise 拒絕並且後來被處理的情況下提供通知。這對於錯誤追蹤和調試非常有用。當一個 Promise 被拒絕後，如果有對應的拒絕處理程序（如 `.catch()` 方法），則會觸發 `onrejectionhandled` 事件。

### 使用方式
`onrejectionhandled` 是一個全局事件，開發者可以通過 `window.onrejectionhandled` 來監聽這個事件：

```javascript
window.onrejectionhandled = function(event) {
    console.log('Promise 被拒絕並已處理:', event.reason);
};
```

### 事件參數
當 `onrejectionhandled` 被觸發時，事件對象包含以下屬性：
- `reason`：表示 Promise 拒絕的原因。

## 範例
以下是 `onrejectionhandled` 的基本使用範例：

### 範例 1：簡單的 Promise 拒絕
```javascript
let myPromise = new Promise((resolve, reject) => {
    reject('發生錯誤！');
});

window.onrejectionhandled = function(event) {
    console.log('Promise 被拒絕並已處理:', event.reason);
};

myPromise.catch(err => {
    console.log('捕獲錯誤:', err);
});
```

### 範例 2：異步操作中的拒絕
```javascript
async function fetchData() {
    throw new Error('數據獲取失敗！');
}

window.onrejectionhandled = function(event) {
    console.log('Promise 被拒絕並已處理:', event.reason);
};

fetchData().catch(err => {
    console.log('捕獲錯誤:', err.message);
});
```

## 解釋
使用 `onrejectionhandled` 事件時，有幾個常見的陷阱和注意事項：

1. **事件不會在所有情況下觸發**：如果 Promise 拒絕後沒有任何處理程序，則不會觸發 `onrejectionhandled`。
2. **只針對已處理的拒絕**：此事件只在 Promise 被處理後才會觸發，對於未處理的拒絕不會有任何通知。
3. **全局範圍**： `onrejectionhandled` 是全局事件，應謹慎使用，以避免影響其他代碼的行為。

## 一句總結
`onrejectionhandled` 事件用於追蹤已處理的 Promise 拒絕，有助於提高錯誤處理的透明度和可調試性。