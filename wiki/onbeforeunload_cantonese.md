<!--
Meta Description: # JavaScript 的 onbeforeunload 事件：使用指南 ## 摘要 `onbeforeunload` 是一個在用戶即將離開網頁時觸發的事件，允許開發者在用戶離開之前顯示提示訊息，幫助用戶防止意外關閉頁面或導航離開。 ## 文件說明 ### 目的 `onbeforeunload` ...
Meta Keywords: onbeforeunload, event, javascript, window, returnvalue
-->

# JavaScript 的 onbeforeunload 事件：使用指南

## 摘要
`onbeforeunload` 是一個在用戶即將離開網頁時觸發的事件，允許開發者在用戶離開之前顯示提示訊息，幫助用戶防止意外關閉頁面或導航離開。

## 文件說明
### 目的
`onbeforeunload` 事件的主要目的是提供用戶一個提示，當他們嘗試關閉或刷新網頁時，可以防止未保存的更改丟失。這對於需要用戶確認的操作特別有用。

### 使用方法
`onbeforeunload` 事件可以透過在 `window` 對象上設置事件處理器來使用。這個事件處理器可以是一個函數，當用戶嘗試離開頁面時，該函數會被調用。

以下是設置 `onbeforeunload` 事件的基本語法：

```javascript
window.onbeforeunload = function (event) {
    event.preventDefault(); // 標準用法
    event.returnValue = ''; // 某些瀏覽器需要設置這個屬性
};
```

### 詳細說明
- **事件觸發**：當用戶嘗試關閉、刷新頁面或導航到其他網址時，`onbeforeunload` 事件會被觸發。
- **提示訊息**：在某些瀏覽器中，用戶將看到一個提示對話框，讓他們確認是否確實要離開。根據最新的瀏覽器政策，這些提示訊息的內容不再可自定義，通常顯示為通用的警告訊息。
- **兼容性**：注意不是所有瀏覽器都支持自定義提示內容。此外，某些瀏覽器可能不會顯示對話框，特別是當用戶的行為被認為是預期的時候。

## 範例
以下是一個簡單的範例，演示如何使用 `onbeforeunload` 事件：

```javascript
window.onbeforeunload = function (event) {
    event.preventDefault(); // 阻止事件的默認行為
    event.returnValue = '你有未保存的更改，是否確定要離開?'; // 提示訊息
};
```

在這個範例中，當用戶嘗試離開頁面時，會彈出一個提示對話框。

## 解釋
- **常見陷阱**：若未設置 `event.returnValue`，某些瀏覽器可能不會顯示任何提示。
- **用戶體驗**：過度使用 `onbeforeunload` 事件可能會影響用戶體驗，建議僅在必要的情況下使用。
- **瀏覽器限制**：由於安全與隱私考量，現代瀏覽器對 `onbeforeunload` 的使用有許多限制，特別是對於自定義提示內容。

## 一句總結
`onbeforeunload` 事件允許開發者在用戶離開網頁前顯示提示訊息，以防止未保存的更改丟失。