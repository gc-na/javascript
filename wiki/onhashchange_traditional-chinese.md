<!--
Meta Description: # onhashchange：JavaScript 網頁哈希變更事件的使用與技巧 ## 簡介 `onhashchange` 是一個 JavaScript 事件，當瀏覽器的 URL 哈希（#後面的部分）發生變更時會被觸發。這個事件對於單頁應用程式（SPA）特別有用，因為它允許開發者在不重新加載頁面的情...
Meta Keywords: onhashchange, window, javascript, url, html
-->

# onhashchange：JavaScript 網頁哈希變更事件的使用與技巧

## 簡介
`onhashchange` 是一個 JavaScript 事件，當瀏覽器的 URL 哈希（#後面的部分）發生變更時會被觸發。這個事件對於單頁應用程式（SPA）特別有用，因為它允許開發者在不重新加載頁面的情況下，根據 URL 的變化來更新顯示內容。

## 文件說明
`onhashchange` 屬性是一個事件處理器，可用於 `window` 物件。當哈希值改變時，會自動觸發此事件。開發者可以通過設置 `onhashchange` 來指定事件發生時的處理函數。

### 目的
- 監控 URL 哈希變化，以便執行相應的操作。
- 提供用戶更好的導航體驗，無需重新加載頁面。

### 使用方法
```javascript
window.onhashchange = function() {
    // 當哈希變更時執行的代碼
    console.log('哈希已改變:', window.location.hash);
};
```

### 詳細說明
- 當哈希值從 `#section1` 變更為 `#section2` 時，`onhashchange` 事件將被觸發。
- 事件處理函數內可以使用 `window.location.hash` 來獲取當前的哈希值。
- `onhashchange` 事件在大多數現代瀏覽器中均被支持，但在一些舊版瀏覽器中可能不支援。

## 範例
### 基本用法
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onhashchange 範例</title>
    <script>
        window.onhashchange = function() {
            console.log('當前哈希:', window.location.hash);
        };
    </script>
</head>
<body>
    <h1>哈希變更示範</h1>
    <a href="#section1">前往 Section 1</a>
    <a href="#section2">前往 Section 2</a>
</body>
</html>
```
在這個範例中，當用戶點擊連結時，控制台會顯示當前的哈希值。

## 說明
- **常見問題**：
  - `onhashchange` 事件在某些瀏覽器中可能不會在頁面首次加載時觸發，因此需要在頁面加載時手動執行一次任何初始化代碼。
  - 如果使用 `setInterval` 或其他方法定期更新哈希，可能會導致過多的事件觸發，影響性能。

- **注意事項**：
  - 使用 `window.onhashchange` 時，確保你的處理函數不會阻塞主執行緒，以免影響用戶體驗。
  - 哈希變更不會導致頁面重新加載，因此需要手動更新視圖以反映當前狀態。

## 一句話總結
`onhashchange` 是一個 JavaScript 事件，當 URL 哈希變更時觸發，適用於提升單頁應用程式的導航體驗。