<!--
Meta Description: # onkeydown 事件在 JavaScript 中的應用 ## 概要 `onkeydown` 是一個用於捕捉鍵盤按下事件的 JavaScript 事件處理器，常用於網頁應用中以提升用戶互動性。 ## 文件說明 `onkeydown` 事件在用戶按下鍵盤上的任意鍵時觸發。它是鍵盤事件序列中的第一...
Meta Keywords: onkeydown, event, html, javascript, head
-->

# onkeydown 事件在 JavaScript 中的應用

## 概要
`onkeydown` 是一個用於捕捉鍵盤按下事件的 JavaScript 事件處理器，常用於網頁應用中以提升用戶互動性。

## 文件說明
`onkeydown` 事件在用戶按下鍵盤上的任意鍵時觸發。它是鍵盤事件序列中的第一個事件，緊接著的是 `onkeypress` 和 `onkeyup`。該事件可用於監聽鍵盤輸入並執行相應的操作。

### 目的
使用 `onkeydown` 事件可以實現以下功能：
- 監控用戶輸入，以進行即時反饋或處理。
- 觸發自定義的功能，如快捷鍵或遊戲控制。
- 提高可用性，改善用戶體驗。

### 用法
`onkeydown` 事件可以直接在 HTML 標籤中使用，也可以通過 JavaScript 設置事件監聽器。其基本語法如下：

```html
<input type="text" id="myInput" onkeydown="myFunction(event)">
```

或使用 JavaScript：

```javascript
document.getElementById("myInput").onkeydown = function(event) {
    myFunction(event);
};
```

## 範例
以下是幾個基本使用範例：

### 範例 1: 基本鍵盤事件捕捉
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>onkeydown 事件範例</title>
</head>
<body>
    <input type="text" id="myInput" onkeydown="handleKey(event)">
    <script>
        function handleKey(event) {
            console.log("按下的鍵: " + event.key);
        }
    </script>
</body>
</html>
```

### 範例 2: 使用快捷鍵
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>快捷鍵範例</title>
</head>
<body>
    <h1>按下 Ctrl + S 來儲存</h1>
    <script>
        document.onkeydown = function(event) {
            if (event.ctrlKey && event.key === 's') {
                event.preventDefault(); // 防止瀏覽器預設行為
                alert("儲存功能已觸發!");
            }
        };
    </script>
</body>
</html>
```

## 解釋
使用 `onkeydown` 時需注意以下幾點：
- 事件的 `key` 屬性返回被按下的鍵的名稱，而 `keyCode` 屬性在某些瀏覽器中已被淘汰，因此建議使用 `key`。
- 此事件在每次按鍵按下時都會觸發，可能會對性能造成影響，尤其是在大量輸入或高頻率使用的情況下。
- 當 `event.preventDefault()` 被調用時，將阻止瀏覽器的預設行為，例如防止表單提交或其它按鍵行為。

## 一句總結
`onkeydown` 是一個用於捕捉鍵盤按下事件的 JavaScript 事件處理器，可增強網頁的互動性與用戶體驗。