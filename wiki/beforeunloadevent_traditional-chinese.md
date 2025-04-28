<!--
Meta Description: # BeforeUnloadEvent：JavaScript 的重要事件處理 ## 簡介 BeforeUnloadEvent 是一個與瀏覽器窗口或標籤頁卸載相關的事件，通常用於在用戶嘗試離開頁面時顯示警告提示。這個事件在用戶關閉標籤頁或導航到其他頁面時被觸發，並使開發者能夠保護用戶不會意外丟失未保存...
Meta Keywords: event, beforeunloadevent, javascript, window, addeventlistener
-->

# BeforeUnloadEvent：JavaScript 的重要事件處理

## 簡介
BeforeUnloadEvent 是一個與瀏覽器窗口或標籤頁卸載相關的事件，通常用於在用戶嘗試離開頁面時顯示警告提示。這個事件在用戶關閉標籤頁或導航到其他頁面時被觸發，並使開發者能夠保護用戶不會意外丟失未保存的數據。

## 文檔
### 目的
BeforeUnloadEvent 旨在讓開發者能夠控制用戶離開當前頁面時的行為，特別是在用戶可能未保存其工作的情況下。

### 使用方法
要使用 BeforeUnloadEvent，開發者可以在 window 對象上添加事件監聽器。以下是基本的用法：

```javascript
window.addEventListener('beforeunload', function (event) {
    // 設置提示信息
    event.preventDefault(); // 這行通常是必需的
    event.returnValue = ''; // 大多數瀏覽器會顯示預設提示
});
```

### 詳細說明
- **event.preventDefault()**：此方法用於告知瀏覽器，您希望在用戶嘗試離開頁面時發出警告。
- **event.returnValue**：設置此屬性可以觸發瀏覽器的確認對話框，許多瀏覽器會忽略自定義的提示文本，而顯示固定的訊息來提醒用戶。
- 當用戶選擇“離開”或“取消”時，事件將相應處理。

## 範例
以下是 BeforeUnloadEvent 的一些基本範例：

### 範例 1：基本用法
```javascript
window.addEventListener('beforeunload', function (event) {
    event.preventDefault();
    event.returnValue = '';
});
```

### 範例 2：檢查未保存的變更
```javascript
let isFormDirty = false;

document.querySelector('form').addEventListener('input', function () {
    isFormDirty = true;
});

window.addEventListener('beforeunload', function (event) {
    if (isFormDirty) {
        event.preventDefault();
        event.returnValue = '';
    }
});
```

## 說明
### 常見陷阱
1. **瀏覽器的行為差異**：不同瀏覽器對 BeforeUnloadEvent 的支持和行為略有不同，特別是在顯示提示信息的方式上。
2. **用戶體驗**：過度使用此事件可能會影響用戶體驗，導致用戶感到困擾。應謹慎使用。

### 注意事項
- 在某些情況下，現代瀏覽器會忽略自定義的提示信息，僅顯示預設的確認對話框。
- 由於安全性考量，某些瀏覽器可能不允許在某些條件下使用 BeforeUnloadEvent。

## 一句總結
BeforeUnloadEvent 允許開發者在用戶嘗試離開頁面時顯示確認對話框，以防止未保存的數據丟失。