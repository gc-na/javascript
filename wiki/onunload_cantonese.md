<!--
Meta Description: # JavaScript 的 onunload 事件：網頁卸載時的處理 ## 概述 `onunload` 是一個 JavaScript 事件，用於在用戶離開當前頁面時觸發特定的函數或代碼。該事件通常用於清理資源、保存狀態或提醒用戶未保存的更改。 ## 文檔 `onunload` 事件會在用戶關閉標籤...
Meta Keywords: onunload, javascript, window, addeventlistener, function
-->

# JavaScript 的 onunload 事件：網頁卸載時的處理

## 概述
`onunload` 是一個 JavaScript 事件，用於在用戶離開當前頁面時觸發特定的函數或代碼。該事件通常用於清理資源、保存狀態或提醒用戶未保存的更改。

## 文檔
`onunload` 事件會在用戶關閉標籤頁、刷新頁面或導航到其他頁面時被觸發。這個事件可以應用於 `window` 對象或特定的 DOM 元素。使用 `onunload` 事件可以幫助開發者進行一些清理工作，確保應用程序或網站的良好運行。

### 用法
要使用 `onunload` 事件，可以將其賦值給 `window` 對象的 `onunload` 屬性，或者使用 `addEventListener` 方法來添加事件監聽器。以下是基本的語法：

```javascript
window.onunload = function(event) {
    // 在這裡執行清理操作
};
```

或者

```javascript
window.addEventListener('unload', function(event) {
    // 在這裡執行清理操作
});
```

## 示例
以下是一些基本的使用示例：

### 示例 1：簡單的卸載事件
```javascript
window.onunload = function() {
    console.log('頁面正在卸載，執行清理操作');
};
```

### 示例 2：使用 addEventListener
```javascript
window.addEventListener('unload', function() {
    alert('你即將離開此頁面！請確認你的更改已保存。');
});
```

### 示例 3：保存用戶數據
```javascript
window.addEventListener('unload', function() {
    localStorage.setItem('lastVisited', new Date().toString());
});
```

## 解釋
使用 `onunload` 時需注意以下幾點：

1. **瀏覽器行為**：某些瀏覽器可能會限制在 `unload` 事件中執行的操作，例如不允許顯示對話框。
2. **性能考量**：過多的操作可能會導致頁面卸載速度變慢，因此應謹慎選擇要執行的操作。
3. **兼容性**：雖然大多數現代瀏覽器都支持 `onunload`，但在某些舊版瀏覽器中可能存在差異。

## 一句總結
`onunload` 事件允許開發者在用戶離開網頁時執行特定的代碼，方便進行資源清理和狀態保存。