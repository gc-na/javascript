<!--
Meta Description: # JavaScript 中的 onkeyup 事件：使用方法與範例 ## 簡介 在 JavaScript 中，`onkeyup` 事件用於處理鍵盤按鍵被釋放時的行為。這個事件可以用來捕捉用戶輸入，並在釋放按鍵後執行特定的操作，適用於表單驗證、即時搜索建議等場景。 ## 文檔 `onkeyup` 是...
Meta Keywords: onkeyup, html, event, javascript, input
-->

# JavaScript 中的 onkeyup 事件：使用方法與範例

## 簡介
在 JavaScript 中，`onkeyup` 事件用於處理鍵盤按鍵被釋放時的行為。這個事件可以用來捕捉用戶輸入，並在釋放按鍵後執行特定的操作，適用於表單驗證、即時搜索建議等場景。

## 文檔
`onkeyup` 是一個 DOM 事件屬性，可用於元素（如 `<input>`、`<textarea>` 等）。當用戶在鍵盤上按下某個鍵並釋放時，會觸發此事件。這使得開發者可以根據用戶的輸入實現即時反饋。

### 用法
要使用 `onkeyup` 事件，開發者可以將其直接設置為 HTML 元素的屬性，或使用 JavaScript 的事件監聽器。以下是這兩種方法的示例：

1. **HTML 方式**:
   ```html
   <input type="text" onkeyup="myFunction()">
   ```

2. **JavaScript 方式**:
   ```javascript
   document.getElementById("myInput").onkeyup = function() {
       myFunction();
   };
   ```

### 詳細說明
- **事件對象**: 在事件處理函數中，可以通過 `event` 參數獲取事件對象，這樣可以獲取更多信息，例如按下的鍵的代碼。
- **鍵盤代碼**: 可以使用 `event.key` 或 `event.keyCode` 來獲取按下的鍵。注意，`keyCode` 在某些情況下已被棄用，建議使用 `event.key`。

## 範例
下面是一些基本的 `onkeyup` 使用範例：

### 基本範例
```html
<!DOCTYPE html>
<html>
<head>
    <title>onkeyup 範例</title>
</head>
<body>
    <input type="text" id="myInput" onkeyup="displayValue()">
    <p id="output"></p>

    <script>
        function displayValue() {
            var input = document.getElementById("myInput").value;
            document.getElementById("output").innerText = input;
        }
    </script>
</body>
</html>
```

### 檢測特定鍵
```html
<!DOCTYPE html>
<html>
<head>
    <title>檢測特定鍵</title>
</head>
<body>
    <input type="text" id="myInput" onkeyup="checkKey(event)">
    <p id="output"></p>

    <script>
        function checkKey(event) {
            if (event.key === "Enter") {
                document.getElementById("output").innerText = "你按下了 Enter 鍵！";
            }
        }
    </script>
</body>
</html>
```

## 解釋
使用 `onkeyup` 事件時，開發者需注意以下幾點：

- **性能問題**: 如果事件處理函數過於複雜，可能會導致性能下降。建議進行防抖（debouncing）或節流（throttling）處理。
- **不同瀏覽器的兼容性**: 雖然大多數現代瀏覽器對 `onkeyup` 的支持良好，但在某些舊版瀏覽器中可能存在不一致行為。
- **鍵盤佈局**: 使用不同的鍵盤佈局時，某些鍵的代碼可能會有所不同，開發者應謹慎處理。

## 總結
`onkeyup` 事件是 JavaScript 中一個強大的工具，能夠在用戶釋放鍵盤按鍵時執行代碼，適合用於即時反饋和交互式應用。