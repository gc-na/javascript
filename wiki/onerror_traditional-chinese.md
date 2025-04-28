<!--
Meta Description: # JavaScript 的 onerror 事件處理器 ## 摘要 `onerror` 是一個 JavaScript 事件處理器，用於捕獲和處理運行時錯誤，特別是在網頁加載過程中的錯誤。這個功能在調試和錯誤處理方面非常重要，能幫助開發者快速識別問題。 ## 文檔 `onerror` 是一個全局事件...
Meta Keywords: onerror, javascript, message, source, lineno
-->

# JavaScript 的 onerror 事件處理器

## 摘要
`onerror` 是一個 JavaScript 事件處理器，用於捕獲和處理運行時錯誤，特別是在網頁加載過程中的錯誤。這個功能在調試和錯誤處理方面非常重要，能幫助開發者快速識別問題。

## 文檔
`onerror` 是一個全局事件處理器，可以用於捕獲 JavaScript 中的錯誤。它通常用於 `<script>` 標籤和 `window` 對象。當發生錯誤時，`onerror` 事件會被觸發，並傳遞錯誤信息，包括錯誤消息、文件名稱和行號。

### 目的
`onerror` 的主要目的是為了提供一種方法來處理未捕獲的錯誤，使開發者能夠在錯誤發生時執行特定的代碼，例如顯示錯誤信息或發送錯誤日誌。

### 用法
要使用 `onerror`，可以將其設置為一個函數，該函數將接收錯誤的詳情。基本語法如下：

```javascript
window.onerror = function(message, source, lineno, colno, error) {
    // 錯誤處理邏輯
};
```

### 參數
- `message`：錯誤消息的描述。
- `source`：發生錯誤的腳本的 URL。
- `lineno`：錯誤發生的行號。
- `colno`：錯誤發生的列號。
- `error`：錯誤對象的實例。

## 範例
以下是 `onerror` 的基本使用範例：

```javascript
window.onerror = function(message, source, lineno, colno, error) {
    console.log("錯誤信息: " + message);
    console.log("發生於: " + source + " 的第 " + lineno + " 行，列 " + colno);
};

// 觸發錯誤
undefinedFunction(); // 這將觸發 onerror 事件
```

## 解釋
使用 `onerror` 時，有幾個常見的陷阱和注意事項：

1. **只捕獲未捕獲的錯誤**：`onerror` 只會捕獲未經處理的錯誤，如果在代碼中使用 `try...catch` 進行捕獲，則不會觸發 `onerror`。

2. **跨域問題**：如果加載的腳本來自不同的域，可能會因為同源策略而無法訪問錯誤的詳細信息。這會導致 `message`、`source`、`lineno` 和 `colno` 的值為 `undefined`。

3. **性能考量**：在生產環境中使用 `onerror` 進行錯誤處理時，需注意性能影響，避免在事件處理器中執行大量的計算。

4. **非同步錯誤**：對於某些非同步錯誤，例如 AJAX 請求中的錯誤，通常需要其他錯誤處理機制。

## 一行總結
`onerror` 是一個強大的 JavaScript 事件處理器，用於捕獲和處理未捕獲的運行時錯誤。