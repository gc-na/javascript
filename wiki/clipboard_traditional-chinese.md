<!--
Meta Description: # JavaScript 剪貼簿功能詳細介紹 ## 摘要 JavaScript 剪貼簿功能允許開發者在網頁應用中讀取和寫入系統剪貼簿，提供用戶更佳的交互體驗。 ## 文檔 剪貼簿功能在 JavaScript 中主要通過 `Clipboard API` 實現，這是一組用於處理剪貼簿內容的接口。這些接口...
Meta Keywords: clipboard, javascript, text, api, navigator
-->

# JavaScript 剪貼簿功能詳細介紹

## 摘要
JavaScript 剪貼簿功能允許開發者在網頁應用中讀取和寫入系統剪貼簿，提供用戶更佳的交互體驗。

## 文檔
剪貼簿功能在 JavaScript 中主要通過 `Clipboard API` 實現，這是一組用於處理剪貼簿內容的接口。這些接口允許開發者在用戶的剪貼簿上執行讀取(讀取剪貼簿內容)和寫入(將內容寫入剪貼簿)的操作。

### 目的
剪貼簿功能使得應用程序可以在用戶的操作之間共享資料，增強用戶體驗，特別是在文本輸入和複製操作的場景中。

### 使用方法
`Clipboard API` 包含以下主要方法：

1. **`navigator.clipboard.writeText(text)`**: 將指定的文本寫入剪貼簿。
2. **`navigator.clipboard.readText()`**: 從剪貼簿中讀取文本內容。

這些方法需要在 HTTPS 環境中運行，或是在 localhost 上進行開發。

## 範例
### 寫入剪貼簿
```javascript
function writeToClipboard(text) {
    navigator.clipboard.writeText(text).then(() => {
        console.log('文本已寫入剪貼簿');
    }).catch(err => {
        console.error('無法寫入剪貼簿: ', err);
    });
}

// 使用範例
writeToClipboard('Hello, World!');
```

### 讀取剪貼簿
```javascript
function readFromClipboard() {
    navigator.clipboard.readText().then(text => {
        console.log('從剪貼簿讀取的文本: ', text);
    }).catch(err => {
        console.error('無法讀取剪貼簿: ', err);
    });
}

// 使用範例
readFromClipboard();
```

## 解釋
使用剪貼簿功能時需注意以下幾點：

- **HTTPS 限制**: `Clipboard API` 只能在安全的上下文中使用，這意味著必須在 HTTPS 協議下運行，否則方法會被拒絕。
- **用戶授權**: 某些瀏覽器可能要求用戶授權才能進行剪貼簿操作，特別是當操作涉及書寫時。
- **兼容性問題**: 雖然大多數現代瀏覽器都支持 `Clipboard API`，但在老舊或某些特定瀏覽器中可能不被支持。

## 一句總結
JavaScript 的剪貼簿功能允許開發者輕鬆地讀取和寫入用戶的剪貼簿，提升應用的交互性和便利性。