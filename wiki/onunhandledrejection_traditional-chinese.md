<!--
Meta Description: # JavaScript 的 onunhandledrejection 事件 ## 概述 `onunhandledrejection` 是 JavaScript 中用於處理未捕獲的 Promise 拒絕（rejection）事件的全局事件處理器。它允許開發者捕捉到未處理的錯誤，並提供一個集中處理這些...
Meta Keywords: onunhandledrejection, promise, javascript, event, reason
-->

# JavaScript 的 onunhandledrejection 事件

## 概述
`onunhandledrejection` 是 JavaScript 中用於處理未捕獲的 Promise 拒絕（rejection）事件的全局事件處理器。它允許開發者捕捉到未處理的錯誤，並提供一個集中處理這些錯誤的機會，以增強錯誤管理和提高應用穩定性。

## 文件說明
### 目的
`onunhandledrejection` 事件的主要目的是在 Promise 拒絕未被處理時，讓開發者能夠介入並執行相應的錯誤處理邏輯。這有助於避免在應用中出現未捕獲的錯誤，從而使應用更為健壯。

### 使用方法
要使用 `onunhandledrejection`，只需將其設置為一個全局事件處理函數，該函數將接收一個事件物件，該物件包含了拒絕的詳細信息。以下是基本的設置方式：

```javascript
window.onunhandledrejection = function(event) {
    console.warn('Unhandled promise rejection:', event.reason);
};
```

### 事件物件
`event` 物件包含以下屬性：
- `reason`: 拒絕的原因，通常是一個錯誤對象或其他信息。
- `promise`: 觸發拒絕的 Promise 對象。

## 示例
以下是使用 `onunhandledrejection` 的基本示例：

```javascript
// 設置未處理拒絕的事件處理器
window.onunhandledrejection = function(event) {
    console.error('未處理的 Promise 拒絕:', event.reason);
};

// 創建一個未處理拒絕的 Promise
new Promise((resolve, reject) => {
    reject(new Error('這是一個錯誤！'));
});
```

在上述代碼中，當 Promise 被拒絕而沒有被捕獲時，`onunhandledrejection` 事件會被觸發，並輸出錯誤信息。

## 解釋
### 常見的陷阱和注意事項
1. **未捕獲的錯誤**: 如果 Promise 被拒絕而沒有任何 `.catch()` 處理，則會觸發 `onunhandledrejection` 事件，這可能會導致應用中的錯誤未被妥善處理。
   
2. **多次觸發**: 如果多個 Promise 拒絕未被捕獲，`onunhandledrejection` 可能會被多次觸發，開發者應在處理時考慮到這一點。

3. **瀏覽器支持**: 幾乎所有現代瀏覽器都支持 `onunhandledrejection`，但在使用前仍需確認目標環境的兼容性。

4. **性能考量**: 在 `onunhandledrejection` 事件中執行重的操作（如 HTTP 請求或長時間運行的計算）可能會影響應用性能，應謹慎處理。

## 總結
`onunhandledrejection` 事件為 JavaScript 提供了一種強大的方式來捕捉未處理的 Promise 拒絕，幫助開發者更好地管理錯誤，從而提升應用的穩定性和用戶體驗。