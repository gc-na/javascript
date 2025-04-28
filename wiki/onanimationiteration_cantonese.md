<!--
Meta Description: # onanimationiteration：JavaScript動畫事件的詳細指南 ## 摘要 `onanimationiteration` 是一個 JavaScript 事件處理器，當 CSS 動畫在元素上重複迭代時觸發。此事件對於需要在動畫過程中進行交互或執行特定操作的開發者來說非常有用。 #...
Meta Keywords: onanimationiteration, javascript, css, html, animatedelement
-->

# onanimationiteration：JavaScript動畫事件的詳細指南

## 摘要
`onanimationiteration` 是一個 JavaScript 事件處理器，當 CSS 動畫在元素上重複迭代時觸發。此事件對於需要在動畫過程中進行交互或執行特定操作的開發者來說非常有用。

## 文檔
### 目的
`onanimationiteration` 事件是用來監聽一個 CSS 動畫的每次迭代。當動畫達到其結束點並重新開始時，該事件將被觸發。這使得開發者可以在動畫過程中執行額外的 JavaScript 操作，例如更新狀態或觸發其他動作。

### 使用方法
要使用 `onanimationiteration`，您需要將事件處理器附加到 DOM 元素。可以通過 JavaScript 直接設置，或在 HTML 標籤中使用屬性設置。

```javascript
const animatedElement = document.getElementById('myElement');

animatedElement.onanimationiteration = function() {
    console.log('動畫迭代完成！');
};
```

### 詳細資訊
- `onanimationiteration` 是一個屬性，可以被設置為一個函數，這個函數在動畫每次重複時執行。
- 可以使用 `animation` 屬性在 CSS 中設置動畫，以及使用 JavaScript 控制動畫的開始和停止。
- 此事件適用於所有支持 CSS 動畫的瀏覽器。

## 示例
### 基本用法
以下是一個簡單的示例，展示如何使用 `onanimationiteration` 事件：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>動畫迭代示例</title>
    <style>
        #myElement {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: move 1s infinite;
        }

        @keyframes move {
            0% { transform: translateX(0); }
            100% { transform: translateX(100px); }
        }
    </style>
</head>
<body>
    <div id="myElement"></div>
    <script>
        const animatedElement = document.getElementById('myElement');

        animatedElement.onanimationiteration = function() {
            console.log('動畫迭代完成！');
        };
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **事件未觸發**：請確保動畫具備 `infinite` 或多次重複的設置，否則事件將不會觸發。
- **性能考量**：在每次迭代中執行大量的 JavaScript 代碼可能會影響性能，建議只執行必要的操作。
- **跨瀏覽器兼容性**：雖然大多數現代瀏覽器支持此事件，但建議測試不同瀏覽器以確保一致性。

## 總結
`onanimationiteration` 事件為開發者提供了一種強大的方式來響應 CSS 動畫的每次重複，從而實現更動態和互動的用戶體驗。