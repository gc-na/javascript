<!--
Meta Description: # JavaScript 的 onunload 事件詳解 ## 摘要 `onunload` 事件在 JavaScript 中用於監聽當用戶離開當前頁面或關閉瀏覽器窗口時所觸發的事件。這對於處理頁面卸載前的清理工作或保存用戶狀態非常有用。 ## 文件說明 `onunload` 事件屬於 Window ...
Meta Keywords: onunload, javascript, window, function, 頁面正在卸載
-->

# JavaScript 的 onunload 事件詳解

## 摘要
`onunload` 事件在 JavaScript 中用於監聽當用戶離開當前頁面或關閉瀏覽器窗口時所觸發的事件。這對於處理頁面卸載前的清理工作或保存用戶狀態非常有用。

## 文件說明
`onunload` 事件屬於 Window 物件，當用戶關閉當前頁面、導航到另一個頁面或重新整理頁面時，這個事件將被觸發。開發者可以利用此事件來執行必要的清理操作，例如取消未完成的請求、保存數據或顯示提示信息。

### 使用方法
`onunload` 事件可以通過以下方式綁定：

```javascript
window.onunload = function() {
    // 事件處理邏輯
};
```

或者使用事件監聽器：

```javascript
window.addEventListener('unload', function() {
    // 事件處理邏輯
});
```

### 事件參數
`onunload` 事件不會接收任何參數，因為它不會被傳遞任何特定的事件對象。

## 範例
以下是 `onunload` 事件的基本使用範例：

```javascript
window.onunload = function() {
    console.log('頁面正在卸載...');
};
```

使用事件監聽器的範例：

```javascript
window.addEventListener('unload', function() {
    console.log('頁面正在卸載...');
});
```

在這些範例中，當用戶試圖離開頁面時，控制台將顯示 "頁面正在卸載..." 的訊息。

## 解釋
### 常見陷阱
1. **性能影響**：在 `onunload` 事件中執行耗時的操作（如 AJAX 請求）可能會導致用戶感受到延遲，因此應避免在卸載事件中進行重的計算或請求。
   
2. **瀏覽器兼容性**：某些瀏覽器對 `onunload` 事件的支持不一致，特別是在行動裝置上，開發者應進行充分測試。

3. **防止頁面關閉提示**：某些瀏覽器允許使用 `onbeforeunload` 事件來顯示離開頁面的提示，這是與 `onunload` 事件不同的，並且通常更加常用於顯示警告。

### 附加說明
- `onunload` 事件無法阻止頁面卸載，若需要在用戶離開時執行某些操作而不希望頁面立即關閉，應使用 `onbeforeunload` 事件。
- 在某些情況下，因安全性考量，瀏覽器可能限制在 `onunload` 中執行某些操作，例如彈出窗口。

## 單句總結
`onunload` 事件允許開發者在用戶離開頁面時執行必要的清理操作，但需謹慎處理以避免影響用戶體驗。