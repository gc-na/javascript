<!--
Meta Description: # ontransitionrun 事件在 JavaScript 中的應用 ## 簡介 `ontransitionrun` 是一個用於監聽 CSS 轉場（transition）開始的事件，當元素的轉場效果開始時會觸發此事件。這個事件對於需要在動畫開始時執行某些操作的開發者來說非常有用。 ## 文檔 ...
Meta Keywords: ontransitionrun, css, box, event, html
-->

# ontransitionrun 事件在 JavaScript 中的應用

## 簡介
`ontransitionrun` 是一個用於監聽 CSS 轉場（transition）開始的事件，當元素的轉場效果開始時會觸發此事件。這個事件對於需要在動畫開始時執行某些操作的開發者來說非常有用。

## 文檔
### 目的
`ontransitionrun` 事件的主要目的是在 CSS 轉場開始時觸發相應的回調函數，讓開發者能夠在轉場過程中進行必要的處理，例如更新 UI 或記錄事件。

### 使用方法
`ontransitionrun` 事件可以被直接設置在 DOM 元素上。當元素的 CSS 轉場開始時，將觸發這個事件。

```javascript
element.ontransitionrun = function(event) {
    console.log('轉場開始:', event);
};
```

### 詳細說明
- **屬性**：`ontransitionrun` 是一個事件處理器屬性，屬於 DOM 元素。
- **觸發時機**：當元素的某個 CSS 屬性因為 transition 而開始變化時，會觸發此事件。
- **事件對象**：傳遞給回調函數的事件對象中包含了有關轉場的詳細信息，例如觸發事件的元素及其當前的樣式狀態。

## 範例
以下是使用 `ontransitionrun` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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
    <title>ontransitionrun 範例</title>
</head>
<body>
    <div class="box" id="myBox"></div>
    <button id="toggle">切換顏色</button>

    <script>
        const box = document.getElementById('myBox');
        const button = document.getElementById('toggle');

        box.ontransitionrun = function(event) {
            console.log('轉場開始:', event.propertyName);
        };

        button.onclick = function() {
            box.classList.toggle('active');
        };
    </script>
</body>
</html>
```

在這個範例中，當用戶按下按鈕時，方塊的顏色將變化，並且在轉場開始時，控制台將顯示該事件的訊息。

## 解釋
- **常見陷阱**：在使用 `ontransitionrun` 事件時，確保元素的 CSS 轉場已正確設定。若沒有設置轉場屬性，事件將不會被觸發。
- **注意事項**：`ontransitionrun` 只會在轉場開始時觸發一次，若需要在轉場過程中持續監聽，應考慮其他事件，例如 `ontransitionend`。

## 一句總結
`ontransitionrun` 是一個有助於監聽 CSS 轉場開始的事件，讓開發者能夠在動畫開始時執行特定操作。