<!--
Meta Description: # JavaScript 中的 oninput 事件：用於即時輸入監聽 ## 概要 `oninput` 是一個 JavaScript 事件，用於監聽用戶在輸入框中輸入數據時的即時變化。這個事件在用戶每次輸入、刪除或修改文本時觸發，提供了一種即時反饋的方式，適合用於表單驗證、搜索建議等功能。 ## 文...
Meta Keywords: oninput, html, input, javascript, const
-->

# JavaScript 中的 oninput 事件：用於即時輸入監聽

## 概要
`oninput` 是一個 JavaScript 事件，用於監聽用戶在輸入框中輸入數據時的即時變化。這個事件在用戶每次輸入、刪除或修改文本時觸發，提供了一種即時反饋的方式，適合用於表單驗證、搜索建議等功能。

## 文檔
### 目的
`oninput` 事件的主要目的是為了能夠在用戶與表單元素交互時，即時捕捉輸入的變化，並根據用戶的輸入即時更新界面或進行驗證。

### 使用方式
`oninput` 事件可以被添加到多種表單元素上，包括 `<input>`、`<textarea>` 和 `<select>`。可以在 HTML 中直接使用屬性來設置，也可以通過 JavaScript 來添加事件監聽器。

#### HTML 示例
```html
<input type="text" id="myInput" oninput="handleInput()">
```

#### JavaScript 示例
```javascript
const inputElement = document.getElementById('myInput');
inputElement.addEventListener('input', handleInput);

function handleInput() {
    console.log(inputElement.value);
}
```

## 範例
以下是使用 `oninput` 的基本範例：

### 基本範例
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>oninput 事件範例</title>
</head>
<body>
    <input type="text" id="myInput" oninput="updateOutput()">
    <p>您輸入的內容是：<span id="output"></span></p>

    <script>
        function updateOutput() {
            const input = document.getElementById('myInput').value;
            document.getElementById('output').textContent = input;
        }
    </script>
</body>
</html>
```

### 進階範例
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>即時搜索建議</title>
</head>
<body>
    <input type="text" id="search" placeholder="搜尋...">
    <div id="suggestions"></div>

    <script>
        const suggestions = ['Apple', 'Banana', 'Orange', 'Grape', 'Mango'];

        document.getElementById('search').addEventListener('input', function() {
            const inputValue = this.value.toLowerCase();
            const filteredSuggestions = suggestions.filter(item => item.toLowerCase().includes(inputValue));
            document.getElementById('suggestions').innerHTML = filteredSuggestions.map(item => `<div>${item}</div>`).join('');
        });
    </script>
</body>
</html>
```

## 解釋
### 常見問題
1. **事件觸發的時機**：`oninput` 事件在用戶每次輸入、刪除或修改文本時觸發，與 `onchange` 事件不同，後者僅在輸入框失去焦點時觸發。
  
2. **性能問題**：在高頻率的事件觸發中（例如用戶快速輸入），可能會導致性能問題。可以考慮使用節流或防抖技術來優化性能。

3. **支援性**：大部分現代瀏覽器均支持 `oninput` 事件，但在較舊的瀏覽器中可能需要考慮使用 `onkeyup` 或 `onkeydown` 事件作為替代方案。

## 一句總結
`oninput` 事件是 JavaScript 中用於即時監聽用戶輸入變化的強大工具，適合用於增強用戶互動和界面反饋。