<!--
Meta Description: # JavaScript 的 onkeydown 事件：鍵盤按下事件的使用指南 ## 簡介 `onkeydown` 是一個 JavaScript 事件，當用戶按下鍵盤上的任意鍵時觸發。這個事件對於需要監控用戶輸入的應用程序特別重要，例如表單驗證或遊戲控制。 ## 文檔 `onkeydown` 事件通...
Meta Keywords: onkeydown, html, event, enter, javascript
-->

# JavaScript 的 onkeydown 事件：鍵盤按下事件的使用指南

## 簡介
`onkeydown` 是一個 JavaScript 事件，當用戶按下鍵盤上的任意鍵時觸發。這個事件對於需要監控用戶輸入的應用程序特別重要，例如表單驗證或遊戲控制。

## 文檔
`onkeydown` 事件通常用於監聽鍵盤按下行為。開發者可以利用這個事件來實現即時反饋或特定功能，例如遊戲中的移動控制。

### 目的
- 監控用戶的鍵盤輸入。
- 實現即時反應，例如在表單中驗證用戶輸入。

### 使用方法
要使用 `onkeydown` 事件，您可以將它附加到 HTML 元素上，如 `<input>` 或 `<textarea>`，或是整個 `window` 對象。

#### 語法範例：
```javascript
element.onkeydown = function(event) {
    // 處理鍵盤按下事件
};
```

## 範例
### 基本使用範例
以下是一個簡單的範例，當用戶按下任意鍵時，顯示所按鍵的代碼：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onkeydown 事件示範</title>
</head>
<body>
    <h1>請按下任意鍵</h1>
    <p id="output"></p>
    
    <script>
        document.onkeydown = function(event) {
            document.getElementById("output").innerText = "你按下的鍵代碼是: " + event.keyCode;
        };
    </script>
</body>
</html>
```

### 另一範例：禁止特定鍵
以下示範如何禁用特定的鍵，例如按下 "Enter" 鍵時不執行任何操作：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>禁止 Enter 鍵</title>
</head>
<body>
    <input type="text" id="inputField" placeholder="請輸入文字">
    
    <script>
        document.getElementById("inputField").onkeydown = function(event) {
            if (event.key === "Enter") {
                event.preventDefault(); // 禁止 Enter 鍵的默認行為
                alert("Enter 鍵被禁用");
            }
        };
    </script>
</body>
</html>
```

## 解釋
使用 `onkeydown` 時需注意以下幾點：
- `onkeydown` 事件在按鍵被按下時觸發，但不會在按鍵被釋放時觸發。要監控鍵釋放事件，可以使用 `onkeyup`。
- 當監控特定鍵時，應使用 `event.key` 而非 `event.keyCode`，因為後者在某些瀏覽器中已被棄用。
- 使用 `event.preventDefault()` 可以防止默認行為，例如防止表單提交。

## 一句總結
`onkeydown` 是一個重要的 JavaScript 事件，允許開發者監控用戶的鍵盤按下行為，從而實現即時反饋及控制。