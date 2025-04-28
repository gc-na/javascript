<!--
Meta Description: # JavaScript 中的焦點 (Focus) 概述與用法 ## 概要 在 JavaScript 中，`focus()` 是一個用於管理 HTML 元素焦點的常用方法。它允許開發者控制用戶界面，增強用戶體驗，特別是在表單和互動元件中。 ## 文件說明 `focus()` 方法是 DOM (Doc...
Meta Keywords: focus, html, javascript, document, input
-->

# JavaScript 中的焦點 (Focus) 概述與用法

## 概要
在 JavaScript 中，`focus()` 是一個用於管理 HTML 元素焦點的常用方法。它允許開發者控制用戶界面，增強用戶體驗，特別是在表單和互動元件中。

## 文件說明
`focus()` 方法是 DOM (Document Object Model) 中的一部分，主要用來將鍵盤焦點設置到指定的 HTML 元素上。當一個元素獲得焦點時，用戶可以直接與該元素進行交互，例如輸入文本框、按鈕或鏈接等。

### 目的
`focus()` 方法的主要目的是提升用戶體驗，確保用戶能夠迅速與重要元素互動。

### 使用方式
`focus()` 方法的語法如下：

```javascript
element.focus();
```

在上面的語法中，`element` 是指要獲得焦點的 DOM 元素，例如一個 `<input>` 或 `<button>`。

### 詳細說明
- **適用對象**：`focus()` 方法可用於所有可聚焦的元素（例如 `<input>`、`<textarea>`、`<button>`、`<a>` 等）。
- **事件觸發**：當元素獲得焦點時，會觸發 `focus` 事件，開發者可以通過事件監聽器來執行相應的操作。
- **兼容性**：此方法在大多數現代瀏覽器中均受支持，但在某些情況下（例如自動獲得焦點）可能會受到瀏覽器安全設置的限制。

## 範例
以下是 `focus()` 方法的基本用法示例：

### 示例 1：在按鈕點擊時聚焦到輸入框
```html
<!DOCTYPE html>
<html>
<head>
    <title>Focus 示例</title>
</head>
<body>
    <input type="text" id="myInput" placeholder="請輸入文字">
    <button id="myButton">聚焦輸入框</button>

    <script>
        document.getElementById("myButton").onclick = function() {
            document.getElementById("myInput").focus();
        };
    </script>
</body>
</html>
```

### 示例 2：自動聚焦
```html
<!DOCTYPE html>
<html>
<head>
    <title>自動聚焦示例</title>
</head>
<body>
    <input type="text" id="autoFocusInput" placeholder="這個輸入框將自動獲得焦點" autofocus>

    <script>
        window.onload = function() {
            document.getElementById("autoFocusInput").focus();
        };
    </script>
</body>
</html>
```

## 解釋
在使用 `focus()` 方法時，開發者應注意以下幾點：

- **自動聚焦的限制**：某些瀏覽器會限制在頁面加載時自動聚焦，特別是當頁面未經用戶交互時。
- **用戶體驗**：過度使用焦點可能會讓用戶感到困惑，應謹慎使用，確保用戶能夠輕鬆地與界面互動。
- **可訪問性**：為了提升可訪問性，建議在適當的時候使用 `focus()`，例如在表單驗證後引導用戶注意錯誤。

## 簡單總結
`focus()` 方法在 JavaScript 中用於設定 HTML 元素的鍵盤焦點，從而增強用戶的交互體驗。