<!--
Meta Description: # JavaScript 的 onload 事件詳解 ## 概述 在 JavaScript 中，`onload` 事件是一個重要的事件，通常用於在網頁或資源（如圖像、腳本和樣式表）完全加載後執行某些操作。通過監聽 `onload` 事件，開發者可以確保所有必要的元素都已經加載，從而避免潛在的錯誤或異...
Meta Keywords: onload, html, javascript, window, body
-->

# JavaScript 的 onload 事件詳解

## 概述
在 JavaScript 中，`onload` 事件是一個重要的事件，通常用於在網頁或資源（如圖像、腳本和樣式表）完全加載後執行某些操作。通過監聽 `onload` 事件，開發者可以確保所有必要的元素都已經加載，從而避免潛在的錯誤或異常行為。

## 文檔
### 目的
`onload` 事件的主要目的是在頁面或資源加載完成後觸發特定的 JavaScript 代碼。這對於確保 DOM 完全可用以及其他資源（如圖像和樣式）正確加載至關重要。

### 用法
`onload` 可以用於 `window` 對象、`document` 對象以及 HTML 元素（如 `<body>`, `<img>` 等）。基本語法如下：

```javascript
window.onload = function() {
    // 在頁面加載完成後執行的代碼
};
```

也可以使用 addEventListener 方法來註冊 `load` 事件：

```javascript
window.addEventListener('load', function() {
    // 在頁面加載完成後執行的代碼
});
```

### 詳細說明
- 當用戶訪問網頁時，瀏覽器會開始加載頁面內容。`onload` 事件會在所有內容（包括圖像、樣式和腳本）加載完成後觸發。
- `onload` 事件的使用通常用於初始化動作，比如設置事件監聽器、啟動動畫，或執行其他需要 DOM 完全加載的操作。

## 範例
### 基本用法範例
1. 使用 `onload` 屬性：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onload 事件範例</title>
    <script>
        window.onload = function() {
            alert('頁面已加載完成！');
        };
    </script>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

2. 使用 `addEventListener` 方法：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onload 事件範例</title>
    <script>
        window.addEventListener('load', function() {
            console.log('頁面已加載完成！');
        });
    </script>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

## 解釋
### 常見陷阱
- **多次註冊**：如果多次為 `onload` 設置函數，後面的函數將覆蓋前面的函數。使用 `addEventListener` 可以避免這一問題，因為它允許多個事件處理器。
- **資源加載問題**：確保所有外部資源（如圖片和腳本）都能正確加載，因為任何加載失敗都可能導致 `onload` 事件無法正常觸發。

### 附加說明
- `onload` 事件僅在所有內容加載完成後觸發，這使得它在某些情況下比 `DOMContentLoaded` 事件要慢，因為後者在 DOM 結構建立完成後立即觸發，而不必等待所有資源加載。

## 一句總結
`onload` 事件用於確保所有網頁內容在執行特定代碼之前已完全加載。