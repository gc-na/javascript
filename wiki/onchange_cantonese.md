<!--
Meta Description: # JavaScript 中的 onchange 事件處理器：全面指南 ## 簡介 `onchange` 事件是 JavaScript 中用於處理表單元素（如輸入框、下拉選單等）值變更的常用事件。當用戶改變某個元素的值並將焦點移開時，`onchange` 事件便會被觸發。 ## 文檔 ### 目的 ...
Meta Keywords: onchange, html, output, javascript, option
-->

# JavaScript 中的 onchange 事件處理器：全面指南

## 簡介
`onchange` 事件是 JavaScript 中用於處理表單元素（如輸入框、下拉選單等）值變更的常用事件。當用戶改變某個元素的值並將焦點移開時，`onchange` 事件便會被觸發。

## 文檔
### 目的
`onchange` 事件旨在幫助開發者監聽用戶對表單元素的變更，從而執行相應的操作，如更新數據、驗證輸入或觸發其他事件。

### 使用方法
`onchange` 事件可直接在 HTML 元素中使用，或通過 JavaScript 來為元素添加事件監聽器。以下是兩種常見的使用方式：

1. **在 HTML 中使用**:
   ```html
   <input type="text" id="myInput" onchange="myFunction()">
   ```

2. **使用 JavaScript 添加事件監聽器**:
   ```javascript
   document.getElementById('myInput').addEventListener('change', myFunction);
   ```

### 事件參數
當 `onchange` 事件被觸發時，事件處理函數會接收一個 `event` 對象，該對象包含了與事件相關的信息。

## 範例
### 基本範例
以下是如何使用 `onchange` 事件的基本示範：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onchange 示例</title>
</head>
<body>
    <select id="mySelect" onchange="displaySelection()">
        <option value="1">選項 1</option>
        <option value="2">選項 2</option>
        <option value="3">選項 3</option>
    </select>
    <p id="output"></p>

    <script>
        function displaySelection() {
            const selectElement = document.getElementById('mySelect');
            const output = document.getElementById('output');
            output.textContent = '你選擇了: ' + selectElement.value;
        }
    </script>
</body>
</html>
```

### 使用 JavaScript 添加事件監聽器的範例
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onchange 示例</title>
</head>
<body>
    <input type="text" id="myInput">
    <p id="output"></p>

    <script>
        document.getElementById('myInput').addEventListener('change', function() {
            const output = document.getElementById('output');
            output.textContent = '輸入的值是: ' + this.value;
        });
    </script>
</body>
</html>
```

## 解釋
### 常見陷阱
- **即時觸發**：`onchange` 事件只有在元素失去焦點後才會觸發，這可能會導致用戶期望在每次輸入時即時反應。對於即時反饋，考慮使用 `oninput` 事件。
- **無法處理所有元素**：某些元素（如 `<input type="checkbox">` 和 `<input type="radio">`）的 `onchange` 事件會在用戶改變狀態時觸發，但在其他情況下可能不會。

## 總結
`onchange` 事件是 JavaScript 中處理用戶輸入變更的重要工具，能夠幫助開發者有效地管理表單數據交互。