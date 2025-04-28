<!--
Meta Description: # ontransitionend：JavaScript 中的過渡結束事件 ## 概述 `ontransitionend` 是一個 JavaScript 事件屬性，用於監聽 CSS 過渡效果結束時的事件。這個事件在元素的 CSS 過渡完成時觸發，使開發者能夠在過渡結束時執行特定的操作。 ## 文檔 ...
Meta Keywords: ontransitionend, javascript, addeventlistener, box, css
-->

# ontransitionend：JavaScript 中的過渡結束事件

## 概述
`ontransitionend` 是一個 JavaScript 事件屬性，用於監聽 CSS 過渡效果結束時的事件。這個事件在元素的 CSS 過渡完成時觸發，使開發者能夠在過渡結束時執行特定的操作。

## 文檔
### 目的
`ontransitionend` 事件的主要目的是讓開發者能夠在 CSS 過渡完成後執行 JavaScript 代碼。無論是改變元素的樣式、更新 DOM 還是觸發其他事件，這個事件都能提供一個合適的時機。

### 使用方法
要使用 `ontransitionend`，你需要將其屬性設置為一個函數，該函數會在過渡結束時被調用。這可以通過直接設置事件處理程序或使用 `addEventListener` 方法來實現。

#### 語法
```javascript
element.ontransitionend = function(event) {
    // 在這裡執行過渡結束後的代碼
};
```
或者使用 `addEventListener`：
```javascript
element.addEventListener('transitionend', function(event) {
    // 在這裡執行過渡結束後的代碼
});
```

## 範例
### 基本使用範例
以下是使用 `ontransitionend` 事件的基本示例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ontransitionend 示例</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .box.active {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="box" id="myBox"></div>
    <button id="toggleButton">切換顏色</button>

    <script>
        const box = document.getElementById('myBox');
        const button = document.getElementById('toggleButton');

        button.addEventListener('click', () => {
            box.classList.toggle('active');
        });

        box.addEventListener('transitionend', () => {
            console.log('過渡結束！');
        });
    </script>
</body>
</html>
```

在這個示例中，當按鈕被點擊時，紅色方塊的背景顏色過渡到藍色，並在過渡結束時輸出訊息。

## 解釋
### 常見陷阱
1. **多重過渡**：如果元素同時有多個過渡，`ontransitionend` 事件將對每個過渡都觸發。為了避免混淆，可以檢查 `event.propertyName` 來確保你只處理特定的過渡。
   
2. **事件未觸發**：如果過渡的 CSS 屬性未正確設置，或者過渡時間為 0，則 `ontransitionend` 事件不會被觸發。

3. **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持 `ontransitionend`，但仍需檢查是否有任何特定的前綴或不兼容情況。

### 額外說明
使用 `addEventListener` 來添加事件處理程序通常被推薦，因為這樣可以在同一元素上添加多個事件處理程序，而不會覆蓋之前的處理程序。

## 一句總結
`ontransitionend` 是一個事件，用於監聽和處理 CSS 過渡效果結束時的操作，使 JavaScript 開發者能夠在過渡完成後執行相應的代碼。