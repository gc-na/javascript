<!--
Meta Description: # JavaScript 中的 onchange 事件處理器 ## 概述 `onchange` 是一個 JavaScript 事件，用於監聽表單元素（如 `<input>`、`<select>` 等）值的變更。當用戶修改這些元素的值並使其失去焦點時，`onchange` 事件會被觸發，從而執行相關的...
Meta Keywords: onchange, html, javascript, option, select
-->

# JavaScript 中的 onchange 事件處理器

## 概述
`onchange` 是一個 JavaScript 事件，用於監聽表單元素（如 `<input>`、`<select>` 等）值的變更。當用戶修改這些元素的值並使其失去焦點時，`onchange` 事件會被觸發，從而執行相關的 JavaScript 代碼。

## 文檔
`onchange` 事件的主要目的是在用戶與表單元素互動後執行特定的動作。這對於需要根據用戶輸入來更新頁面內容或進行數據驗證的情況特別有用。

### 使用方法
要使用 `onchange` 事件，可以在 HTML 標籤中直接添加 `onchange` 屬性，或使用 JavaScript 的事件監聽器來添加。

#### HTML 標籤方式
```html
<input type="text" onchange="myFunction()">
```

#### JavaScript 事件監聽器方式
```javascript
document.getElementById("myInput").onchange = function() {
    myFunction();
};
```

在這裡，`myFunction` 是當事件被觸發時執行的函數。

## 範例
### 基本用法
以下是一個簡單的範例，當用戶在輸入框中輸入內容並失去焦點時，會顯示一條消息。

```html
<!DOCTYPE html>
<html>
<head>
    <title>onchange 事件範例</title>
</head>
<body>

<input type="text" id="myInput" onchange="displayMessage()">

<script>
function displayMessage() {
    alert("您輸入的內容已更改！");
}
</script>

</body>
</html>
```

### 使用 select 元素
以下範例顯示如何在 `<select>` 下拉選單中使用 `onchange` 事件：

```html
<!DOCTYPE html>
<html>
<head>
    <title>onchange 事件範例</title>
</head>
<body>

<select id="mySelect" onchange="showSelection()">
    <option value="apple">蘋果</option>
    <option value="banana">香蕉</option>
    <option value="cherry">櫻桃</option>
</select>

<script>
function showSelection() {
    alert("您選擇的水果是：" + document.getElementById("mySelect").value);
}
</script>

</body>
</html>
```

## 解釋
### 常見陷阱
1. **事件觸發時機**: `onchange` 事件只在元素失去焦點時觸發，這意味著用戶在輸入框中輸入內容後，若不點擊其他地方，事件將不會被觸發。
2. **對於 checkbox 和 radio**: 對於這些元素，`onchange` 事件在選擇狀態變化時會立即觸發，而不需失去焦點。
3. **多次觸發**: 確保在添加事件監聽器時不會重複添加，這可能導致函數被多次調用。

## 一句話總結
`onchange` 是一個用於監聽表單元素值變更的事件，能夠幫助開發者根據用戶輸入即時執行 JavaScript 代碼。