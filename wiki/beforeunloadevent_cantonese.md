<!--
Meta Description: # BeforeUnloadEvent 在 JavaScript 中的應用與使用 ## 簡介 BeforeUnloadEvent 係一個重要的 JavaScript 事件，當用戶嘗試離開當前頁面時觸發，通常用來提示用戶保存未完成的工作。 ## 文件說明 BeforeUnloadEvent 主要用於監...
Meta Keywords: event, beforeunloadevent, javascript, window, addeventlistener
-->

# BeforeUnloadEvent 在 JavaScript 中的應用與使用

## 簡介
BeforeUnloadEvent 係一個重要的 JavaScript 事件，當用戶嘗試離開當前頁面時觸發，通常用來提示用戶保存未完成的工作。

## 文件說明
BeforeUnloadEvent 主要用於監聽用戶的離開行為。當用戶關閉瀏覽器、刷新頁面或導航到其他網址時，這個事件可以讓開發者顯示提示，提醒用戶確認是否真的要離開。這樣可以有效防止用戶因為不小心而丟失重要數據。

### 目的
- 提醒用戶在離開之前保存其正在進行的工作。
- 增強用戶體驗，減少數據丟失的情況。

### 使用方法
要使用 BeforeUnloadEvent，你可以在 `window` 對象上加上事件監聽器。這是基本語法：
```javascript
window.addEventListener('beforeunload', function (event) {
    event.preventDefault(); // 標準的做法
    event.returnValue = ''; // 為了某些瀏覽器的兼容性
});
```

## 範例
以下是如何使用 BeforeUnloadEvent 的基本範例：

### 範例 1：基本提示
```javascript
window.addEventListener('beforeunload', function (event) {
    event.preventDefault(); // 阻止默認行為
    event.returnValue = ''; // 提示用戶
});
```

### 範例 2：在表單中使用
```javascript
const form = document.querySelector('form');

form.addEventListener('submit', function() {
    window.removeEventListener('beforeunload', beforeUnloadHandler);
});

window.addEventListener('beforeunload', beforeUnloadHandler);

function beforeUnloadHandler(event) {
    event.preventDefault();
    event.returnValue = '';
}
```

## 解釋
### 常見陷阱
1. **不必要的提示**：如果用戶已經保存了所有更改，則不應該顯示提示。
2. **不支持的瀏覽器行為**：某些瀏覽器對 `event.returnValue` 的處理不同，可能不會顯示自定義消息。
3. **用戶體驗**：過於頻繁的提示可能會讓用戶感到困擾，因此應該謹慎使用。

### 額外註解
- 當事件被觸發時，瀏覽器會顯示一個默認的提示對話框，具體內容可能因瀏覽器而異。
- 在某些情況下，例如在網頁未完成加載時，可能無法顯示此事件。

## 總結
BeforeUnloadEvent 係 JavaScript 中一個重要的事件，用於提醒用戶在離開頁面時保存未完成的工作，以增強用戶體驗。