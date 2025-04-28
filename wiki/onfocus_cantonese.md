<!--
Meta Description: # JavaScript 的 onfocus 事件：全面指南 ## 簡介 `onfocus` 是 JavaScript 中的一個事件處理程序，用於監聽元素（如輸入框、文本區等）獲得焦點的情況。當使用者點擊或導航到該元素時，`onfocus` 事件會被觸發，這使得開發者能夠執行特定的代碼，增強用戶體驗...
Meta Keywords: onfocus, html, javascript, myinput, input
-->

# JavaScript 的 onfocus 事件：全面指南

## 簡介
`onfocus` 是 JavaScript 中的一個事件處理程序，用於監聽元素（如輸入框、文本區等）獲得焦點的情況。當使用者點擊或導航到該元素時，`onfocus` 事件會被觸發，這使得開發者能夠執行特定的代碼，增強用戶體驗。

## 文檔
### 目的
`onfocus` 事件的主要目的是讓開發者能夠捕捉到用戶與輸入元素的互動，並在用戶開始輸入時執行特定的操作，例如顯示提示信息、改變樣式或驗證輸入等。

### 使用方法
`onfocus` 事件可以通過 HTML 屬性或 JavaScript 代碼來添加。以下是兩種常見使用方法：

1. **HTML 屬性方式**：
   ```html
   <input type="text" onfocus="myFunction()">
   ```

2. **JavaScript 代碼方式**：
   ```javascript
   const inputElement = document.getElementById('myInput');
   inputElement.onfocus = function() {
       myFunction();
   };
   ```

### 詳細說明
- **觸發條件**：當元素獲得焦點時觸發，通常由用戶的點擊或鍵盤導航（如 Tab 鍵）引起。
- **可用於哪些元素**：主要用於表單元素，如 `<input>`、`<textarea>` 和 `<select>`。
- **事件對象**：`onfocus` 事件會傳遞一個事件對象，該對象提供了當前事件的詳細信息。
- **取消焦點**：為了移除焦點，可以使用 `blur()` 方法。

## 範例
以下是幾個簡單的使用範例：

### 範例 1：基本用法
```html
<!DOCTYPE html>
<html>
<head>
    <title>onfocus 範例</title>
</head>
<body>
    <input type="text" id="myInput" onfocus="alert('獲得焦點!')">
</body>
</html>
```

### 範例 2：使用 JavaScript 設置
```html
<!DOCTYPE html>
<html>
<head>
    <title>onfocus 範例</title>
    <script>
        function highlightInput() {
            document.getElementById('myInput').style.backgroundColor = 'yellow';
        }
    </script>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        document.getElementById('myInput').onfocus = highlightInput;
    </script>
</body>
</html>
```

## 解釋
- **常見陷阱**：確保事件處理程序不會意外觸發多次，特別是在使用動態創建的元素時。
- **兼容性問題**：某些舊版瀏覽器可能不完全支持 `onfocus` 事件，建議使用最新的瀏覽器進行測試。
- **焦點管理**：在複雜的表單中，適當的焦點管理可以提升用戶體驗，通過使用 `onblur` 事件來處理失去焦點的情況。

## 一句總結
`onfocus` 事件在 JavaScript 中用於捕捉用戶對輸入元素的焦點行為，提升互動性和用戶體驗。