<!--
Meta Description: # JavaScript 的 onbeforeunload 事件：使用者離開頁面時的警示功能 ## 摘要 `onbeforeunload` 是一個 JavaScript 事件，允許開發者在使用者嘗試離開當前頁面或重新整理時顯示警告訊息，以防止未儲存的變更或數據遺失。 ## 文件說明 `onbefor...
Meta Keywords: onbeforeunload, message, event, javascript, window
-->

# JavaScript 的 onbeforeunload 事件：使用者離開頁面時的警示功能

## 摘要
`onbeforeunload` 是一個 JavaScript 事件，允許開發者在使用者嘗試離開當前頁面或重新整理時顯示警告訊息，以防止未儲存的變更或數據遺失。

## 文件說明
`onbeforeunload` 事件在使用者即將離開當前頁面時觸發，這可以是關閉瀏覽器、導航到另一個網址或重新整理頁面。此事件可用來提醒使用者，讓他們確認是否真的想要離開，特別是在表單未完成或數據尚未儲存的情況下。

### 使用方式
要使用 `onbeforeunload` 事件，可以在 `window` 物件上設置事件監聽器。以下是基本的使用方式：

```javascript
window.onbeforeunload = function(event) {
    var message = "您有未儲存的變更，確定要離開嗎？";
    event.returnValue = message; // 這行代碼在某些瀏覽器中是必須的
    return message; // 瀏覽器會顯示這個提示
};
```

### 事件細節
- **觸發時機**：當使用者嘗試關閉頁面、重新整理或導航到其他網址時。
- **回傳值**：`event.returnValue` 和函數的返回值都可以設定顯示的提示訊息。
- **限制**：大多數現代瀏覽器對於自定義提示訊息有嚴格的限制，通常會顯示預設的警告訊息，而不會顯示開發者所提供的內容。

## 範例
以下是一些使用 `onbeforeunload` 的範例：

### 基本範例
```javascript
window.onbeforeunload = function(event) {
    var message = "您有未儲存的變更，確定要離開嗎？";
    event.returnValue = message; // 設定警示消息
    return message; // 返回消息以顯示警示
};
```

### 結合表單
```javascript
var isFormDirty = false;

document.getElementById("myForm").addEventListener("input", function() {
    isFormDirty = true; // 當使用者修改表單時
});

window.onbeforeunload = function(event) {
    if (isFormDirty) {
        var message = "您有未儲存的變更，確定要離開嗎？";
        event.returnValue = message;
        return message;
    }
};
```

## 說明
- **常見陷阱**：某些瀏覽器在處理 `onbeforeunload` 時會忽略自定義的提示訊息，只顯示預設的警告內容。這是為了防止惡意網站濫用此功能。
- **使用者體驗**：過於頻繁地使用 `onbeforeunload` 會影響使用者體驗，應該謹慎使用，避免不必要的干擾。
- **最小化使用**：應該僅在確保有未儲存的變更時才觸發此事件，避免在每次頁面切換時都顯示警告。

## 總結
`onbeforeunload` 事件是一個重要的工具，用於在使用者嘗試離開頁面時提醒他們未儲存的變更，適當使用可增強應用程序的穩定性和使用者體驗。