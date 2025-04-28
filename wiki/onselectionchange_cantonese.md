<!--
Meta Description: # onselectionchange：JavaScript 中的選擇變更事件 ## 簡介 `onselectionchange` 是一個 JavaScript 事件，用於監聽用戶在文檔中選擇文本或元素時的變更。該事件通常用於增強用戶體驗，讓開發者能夠對用戶的選擇做出即時反應。 ## 文檔 ### ...
Meta Keywords: onselectionchange, javascript, document, html, selection
-->

# onselectionchange：JavaScript 中的選擇變更事件

## 簡介
`onselectionchange` 是一個 JavaScript 事件，用於監聽用戶在文檔中選擇文本或元素時的變更。該事件通常用於增強用戶體驗，讓開發者能夠對用戶的選擇做出即時反應。

## 文檔
### 目的
`onselectionchange` 事件的主要目的是當用戶在網頁上選擇內容時觸發特定的功能。這可以用於文本編輯器、網頁應用程式或任何需要動態響應用戶選擇的場景。

### 用法
`onselectionchange` 事件可以綁定到 `document` 對象上。當用戶改變選擇的文本或元素時，該事件會被觸發。開發者可以使用 JavaScript 來定義事件處理函數，以便在選擇變更時執行特定的操作。

#### 語法
```javascript
document.onselectionchange = function() {
    // 事件處理程式
};
```

### 詳細說明
- 事件會在用戶選擇內容後立即觸發，這意味著開發者可以獲取當前的選擇範圍。
- 可以使用 `window.getSelection()` 方法來獲取當前的選擇範圍對象，該對象提供了關於選擇的詳細信息，包括選擇的文本、起始和結束位置等。

## 範例
### 基本用法
以下是一個簡單的範例，展示如何使用 `onselectionchange` 事件來顯示當前選擇的文本。

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onselectionchange 範例</title>
</head>
<body>
    <p>請選擇這段文字以查看選擇的內容。</p>
    <div id="output"></div>

    <script>
        document.onselectionchange = function() {
            const selection = window.getSelection().toString();
            document.getElementById('output').textContent = selection ? `你選擇了：${selection}` : '';
        };
    </script>
</body>
</html>
```

## 解釋
### 常見陷阱
- **事件未適用於所有瀏覽器**：某些舊版瀏覽器可能不支持 `onselectionchange` 事件，因此在開發時應考慮兼容性問題。
- **性能考量**：在高頻率觸發的事件中，例如用戶快速選擇文本時，過於複雜的處理函數可能導致性能下降，建議使用防抖或節流技術來優化性能。

### 額外注意事項
- 確保在事件處理函數中正確處理空選擇的情況，以避免不必要的錯誤或空白輸出。
- 在某些情況下，選擇的變更可能不會立即反映在 DOM 中，因此需要考慮使用異步方法來處理更新。

## 一句總結
`onselectionchange` 是一個強大的事件，允許開發者在用戶選擇內容時即時作出反應，增強網頁的互動性。