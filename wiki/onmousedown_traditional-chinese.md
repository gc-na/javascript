<!--
Meta Description: # onmousedown 事件：JavaScript 中的鼠標按下事件 ## 摘要 `onmousedown` 是一個 JavaScript 事件，用於監聽用戶在元素上按下鼠標按鍵的動作。這個事件對於創建互動式網頁應用非常重要，因為它允許開發者在用戶與界面進行交互時執行特定的操作。 ## 文件說明...
Meta Keywords: onmousedown, html, event, javascript, button
-->

# onmousedown 事件：JavaScript 中的鼠標按下事件

## 摘要
`onmousedown` 是一個 JavaScript 事件，用於監聽用戶在元素上按下鼠標按鍵的動作。這個事件對於創建互動式網頁應用非常重要，因為它允許開發者在用戶與界面進行交互時執行特定的操作。

## 文件說明
`onmousedown` 事件在用戶按下鼠標按鍵時觸發。它可以用於各種 HTML 元素，並且可以與 JavaScript 函數結合使用，以創建響應式的用戶界面。該事件的使用方式如下：

### 語法
```javascript
element.onmousedown = function(event) {
    // 事件處理代碼
};
```

### 事件對象
當事件被觸發時，將傳遞一個事件對象 `event`，該對象包含有關事件的詳細信息，例如：
- `button`: 被按下的鼠標按鍵（0 - 左鍵，1 - 中鍵，2 - 右鍵）
- `clientX` 和 `clientY`: 鼠標指針相對於視口的坐標

## 範例
以下是 `onmousedown` 事件的基本用法示例：

### 示例 1：簡單的按下事件
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>onmousedown 範例</title>
</head>
<body>
    <button id="myButton">按下我</button>
    <script>
        document.getElementById("myButton").onmousedown = function(event) {
            alert("鼠標按下！按鍵編號：" + event.button);
        };
    </script>
</body>
</html>
```

### 示例 2：獲取鼠標位置
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>onmousedown 範例</title>
</head>
<body>
    <div id="myDiv" style="width: 200px; height: 200px; background-color: lightblue;"></div>
    <script>
        document.getElementById("myDiv").onmousedown = function(event) {
            console.log("鼠標位置：(" + event.clientX + ", " + event.clientY + ")");
        };
    </script>
</body>
</html>
```

## 解釋
在使用 `onmousedown` 事件時，開發者需注意以下幾點：
- 事件可能會與其他鼠標事件（如 `onmouseup` 和 `onclick`）一起使用，這可能會導致意外的行為。因此，在處理事件時應小心設計邏輯。
- 確保在適當的元素上使用該事件，以避免無效的觸發。
- 在某些情況下，若事件處理程序需要進一步處理，考慮使用 `event.preventDefault()` 來阻止預設行為。

## 一句話總結
`onmousedown` 是一個用於捕捉用戶在元素上按下鼠標按鍵的 JavaScript 事件，對於創建交互式網頁應用至關重要。