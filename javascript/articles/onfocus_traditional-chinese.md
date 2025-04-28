<!--
Meta Description: # 在 JavaScript 中的 onfocus 事件：用法與範例 ## 簡介 `onfocus` 是一種事件處理器，用於當 HTML 元素（例如輸入框或文本區）獲得焦點時觸發指定的 JavaScript 代碼。這個事件在網頁表單的用戶互動中非常重要，能夠改善用戶體驗。 ## 文檔 ### 目的 ...
Meta Keywords: onfocus, html, javascript, input, inputfield
-->

# 在 JavaScript 中的 onfocus 事件：用法與範例

## 簡介
`onfocus` 是一種事件處理器，用於當 HTML 元素（例如輸入框或文本區）獲得焦點時觸發指定的 JavaScript 代碼。這個事件在網頁表單的用戶互動中非常重要，能夠改善用戶體驗。

## 文檔
### 目的
`onfocus` 事件的主要目的是監聽特定元素的焦點變化，以便執行相應的操作，例如顯示提示訊息、改變元素的樣式或執行表單驗證。

### 用法
`onfocus` 事件可以通過 HTML 的事件屬性或 JavaScript 的事件監聽器來使用。以下是基本的語法：

#### HTML 屬性方式
```html
<input type="text" onfocus="myFunction()">
```

#### JavaScript 監聽器方式
```javascript
const inputField = document.getElementById('myInput');
inputField.addEventListener('focus', myFunction);
```

### 詳細說明
- **觸發條件**：當元素獲得焦點時，`onfocus` 事件會被觸發。這通常發生在用戶點擊輸入框或使用鍵盤導航時。
- **支援的元素**：`onfocus` 事件通常用於表單元素，如 `<input>`、`<textarea>` 和 `<select>` 等。
- **相對的事件**：與 `onfocus` 事件相對應的是 `onblur` 事件，當元素失去焦點時會觸發。

## 範例
### 基本用法範例
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onfocus 事件範例</title>
    <script>
        function showMessage() {
            alert('輸入框已獲得焦點！');
        }
    </script>
</head>
<body>
    <input type="text" onfocus="showMessage()">
</body>
</html>
```

### 使用 JavaScript 監聽器的範例
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onfocus 事件範例</title>
    <script>
        window.onload = function() {
            const inputField = document.getElementById('myInput');
            inputField.addEventListener('focus', function() {
                console.log('輸入框已獲得焦點！');
            });
        };
    </script>
</head>
<body>
    <input type="text" id="myInput">
</body>
</html>
```

## 解釋
- **常見陷阱**：在使用 `onfocus` 時，請確保事件處理函數已正確定義，否則會導致錯誤或無法觸發事件。
- **跨瀏覽器支援**：`onfocus` 事件在主流瀏覽器中被廣泛支持，但某些舊版瀏覽器可能存在不一致的行為。
- **樣式變化**：使用 `onfocus` 可以結合 CSS 來改變元素的樣式，提高用戶的互動體驗。例如，當輸入框獲得焦點時，可以改變邊框顏色。

## 總結
`onfocus` 事件是一個強大且實用的工具，可用於提高用戶在 web 表單中的互動性與體驗，當元素獲得焦點時，能夠執行自定義的 JavaScript 代碼。