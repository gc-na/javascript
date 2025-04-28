<!--
Meta Description: # onhashchange：JavaScript 中的哈希變更事件 ## 概述 `onhashchange` 是一個 JavaScript 事件，用於監聽 URL 哈希部分的變更。當瀏覽器的地址欄中的哈希值改變時，該事件會被觸發，這對於單頁應用（SPA）特別有用，因為它可以用來管理不同的視圖而不需...
Meta Keywords: onhashchange, window, javascript, html, contentdiv
-->

# onhashchange：JavaScript 中的哈希變更事件

## 概述
`onhashchange` 是一個 JavaScript 事件，用於監聽 URL 哈希部分的變更。當瀏覽器的地址欄中的哈希值改變時，該事件會被觸發，這對於單頁應用（SPA）特別有用，因為它可以用來管理不同的視圖而不需要重新載入頁面。

## 文件說明
### 目的
`onhashchange` 事件允許開發者在哈希值變更時執行特定的 JavaScript 程式碼。這對於需要根據用戶導航改變頁面內容的應用程序非常重要。

### 使用方法
要使用 `onhashchange`，只需將事件處理函數賦值給 `window.onhashchange`。當哈希值發生變更時，該函數將被自動調用。

### 語法
```javascript
window.onhashchange = function() {
    // 處理哈希變更的代碼
};
```

## 示例
### 基本用法
以下是一個簡單的範例，當哈希變更時，會在控制台顯示新的哈希值：

```javascript
window.onhashchange = function() {
    console.log("新的哈希值是: " + window.location.hash);
};

// 模擬哈希變更
window.location.hash = "newHash";
```

### 更改頁面內容
這是一個使用 `onhashchange` 來改變頁面內容的例子：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onhashchange 示例</title>
</head>
<body>
    <div id="content">請選擇一個哈希來顯示內容。</div>
    <script>
        window.onhashchange = function() {
            const contentDiv = document.getElementById('content');
            switch (window.location.hash) {
                case '#home':
                    contentDiv.innerHTML = '歡迎來到首頁！';
                    break;
                case '#about':
                    contentDiv.innerHTML = '這是關於我們的頁面。';
                    break;
                default:
                    contentDiv.innerHTML = '請選擇一個有效的哈希。';
            }
        };
    </script>
</body>
</html>
```

## 解釋
### 常見問題
1. **瀏覽器支持**：`onhashchange` 在所有現代瀏覽器中均受到支持，但在某些舊版瀏覽器中可能不兼容。
2. **多次觸發**：如果在同一個哈希變更操作中多次修改哈希，`onhashchange` 只會觸發一次。因此，開發者需要考慮這一點，以避免重複執行相同的操作。

### 附加注意事項
- `onhashchange` 只對哈希部分的變更有效，對於 URL 的其他部分（例如查詢字符串）則不會觸發。
- 對於單頁應用，使用 `pushState` 或 `replaceState` 結合 `onhashchange` 可提供更靈活的導航解決方案。

## 一句總結
`onhashchange` 事件允許開發者在 URL 哈希變更時執行特定操作，是管理單頁應用導航的重要工具。