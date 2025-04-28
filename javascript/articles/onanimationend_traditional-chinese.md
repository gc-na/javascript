<!--
Meta Description: # onanimationend 事件：JavaScript 動畫結束監聽的完整指南 ## 簡介 `onanimationend` 是一個用於監聽 CSS 動畫結束事件的 JavaScript 事件屬性。當一個 CSS 動畫完成播放後，這個事件會被觸發，允許開發者在動畫結束時執行特定的 JavaSc...
Meta Keywords: onanimationend, javascript, element, css, function
-->

# onanimationend 事件：JavaScript 動畫結束監聽的完整指南

## 簡介
`onanimationend` 是一個用於監聽 CSS 動畫結束事件的 JavaScript 事件屬性。當一個 CSS 動畫完成播放後，這個事件會被觸發，允許開發者在動畫結束時執行特定的 JavaScript 程式碼。

## 文件說明
`onanimationend` 事件在動畫結束時被觸發，這對於需要在動畫完成後進行某些操作的情況非常有用。使用此事件，可以輕鬆地添加動畫結束後的行為，例如移除動畫類別、啟動下一個動畫或觸發其他事件。

### 使用方法
在 JavaScript 中，您可以通過以下方式來使用 `onanimationend` 事件：

```javascript
element.onanimationend = function(event) {
    // 動畫結束後執行的程式碼
};
```

您也可以使用 `addEventListener` 方法來添加事件監聽器：

```javascript
element.addEventListener('animationend', function(event) {
    // 動畫結束後執行的程式碼
});
```

### 事件屬性
- `animationName`：觸發事件的動畫名稱。
- `elapsedTime`：動畫運行的時間（以秒為單位）。
- `pseudoElement`：觸發事件的偽元素（如 `::before` 或 `::after`）。

## 範例
### 基本範例
以下是使用 `onanimationend` 事件的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animation End Example</title>
    <style>
        .animate {
            animation: fadeOut 2s forwards;
        }

        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }
    </style>
</head>
<body>
    <div id="myElement" class="animate">這是動畫元素</div>
    <script>
        const element = document.getElementById('myElement');
        element.onanimationend = function() {
            alert('動畫結束了！');
        };
    </script>
</body>
</html>
```

### 使用 `addEventListener`
```javascript
const element = document.getElementById('myElement');
element.addEventListener('animationend', function(event) {
    console.log('動畫 "' + event.animationName + '" 已結束。');
});
```

## 解釋
在使用 `onanimationend` 事件時，有一些常見的陷阱和注意事項：

1. **多次觸發**：如果元素上有多個動畫，`onanimationend` 可能會被觸發多次。確保根據動畫名稱來識別特定的動畫結束事件。
2. **CSS 兼容性**：某些舊瀏覽器可能不支持 CSS 動畫，這可能導致事件無法正常工作。建議檢查瀏覽器兼容性。
3. **偽元素**：如果動畫涉及偽元素（如 `::before` 或 `::after`），則 `pseudoElement` 屬性會有用，可以幫助識別具體的動畫來源。

## 總結
`onanimationend` 事件是一個強大的工具，用於在 CSS 動畫完成後執行 JavaScript 代碼，能夠增強用戶體驗並提高網站的互動性。