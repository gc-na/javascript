<!--
Meta Description: # JavaScript 的 `onunhandledrejection`: 監聽未處理的 Promise 拒絕 ## 簡介 `onunhandledrejection` 是一個全局事件，用於監聽 Promise 的未處理拒絕（unhandled rejection）。當一個 Promise 被拒絕...
Meta Keywords: onunhandledrejection, promise, event, javascript, window
-->

# JavaScript 的 `onunhandledrejection`: 監聽未處理的 Promise 拒絕

## 簡介
`onunhandledrejection` 是一個全局事件，用於監聽 Promise 的未處理拒絕（unhandled rejection）。當一個 Promise 被拒絕但沒有被適當的處理時，這個事件將被觸發。這有助於開發者捕捉錯誤並進行適當的錯誤處理。

## 文檔
### 目的
`onunhandledrejection` 事件的主要目的是讓開發者能夠捕捉並處理那些在 Promise 內部拒絕但未被捕獲的錯誤。它提供了一個機會來記錄錯誤、顯示通知或者進行其他自定義的錯誤處理。

### 使用方法
要使用 `onunhandledrejection`，您需要將一個事件處理函數分配給 `window.onunhandledrejection`。該處理函數將接收一個事件對象，其中包含有關未處理拒絕的詳細信息。

#### 語法
```javascript
window.onunhandledrejection = function(event) {
    // 錯誤處理邏輯
    console.error(event.reason); // 錯誤原因
};
```

### 詳細說明
- `event.reason`: 包含未處理拒絕的值，通常是錯誤對象。
- `event.promise`: 代表未處理拒絕的 Promise 對象。

這個事件可以幫助您更好地了解應用程序中的錯誤和異常情況，並在出現問題時提供用戶更好的反饋。

## 示例
### 基本用法
```javascript
window.onunhandledrejection = function(event) {
    console.error("未處理的拒絕:", event.reason);
};

const myPromise = new Promise((resolve, reject) => {
    reject(new Error("這是一個錯誤"));
});

// 此 Promise 的拒絕未被捕獲，將觸發 `onunhandledrejection`
```

### 進階用法
```javascript
window.onunhandledrejection = function(event) {
    alert("捕捉到未處理的拒絕: " + event.reason.message);
};

const faultyPromise = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            reject(new Error("異步錯誤"));
        }, 1000);
    });
};

faultyPromise(); // 這會在一秒後觸發未處理的拒絕
```

## 解釋
### 常見問題
1. **為什麼會出現未處理拒絕？**
   - 當一個 Promise 被拒絕但沒有使用 `.catch()` 或 `try/catch` 來處理時，將會出現未處理拒絕。

2. **如何避免未處理拒絕？**
   - 確保每個 Promise 都有適當的錯誤處理，例如使用 `.catch()` 方法。

3. **`onunhandledrejection` 會在所有瀏覽器中都可用嗎？**
   - 大多數現代瀏覽器都支持這個事件，但在使用前應檢查兼容性。

### 陷阱
- 如果不處理 `onunhandledrejection` 事件，某些瀏覽器可能會顯示警告或錯誤消息，影響用戶體驗。

## 一句話總結
`onunhandledrejection` 事件允許開發者捕捉和處理未處理的 Promise 拒絕，以改善錯誤處理和用戶體驗。