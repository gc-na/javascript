<!--
Meta Description: # oncontextmenu: JavaScript 右鍵菜單事件的全面指南 ## 摘要 `oncontextmenu` 是一個 JavaScript 事件屬性，允許開發者在用戶右鍵點擊時自定義行為。此事件常用於禁用瀏覽器的默認右鍵菜單，或在特定情境下顯示自定義菜單。 ## 文檔 ### 目的 `...
Meta Keywords: event, html, oncontextmenu, div, style
-->

# oncontextmenu: JavaScript 右鍵菜單事件的全面指南

## 摘要
`oncontextmenu` 是一個 JavaScript 事件屬性，允許開發者在用戶右鍵點擊時自定義行為。此事件常用於禁用瀏覽器的默認右鍵菜單，或在特定情境下顯示自定義菜單。

## 文檔
### 目的
`oncontextmenu` 事件在用戶右鍵點擊元素時觸發。這使得開發者能夠控制用戶在該元素上右鍵點擊時的行為，通常用於自定義上下文菜單或防止默認行為（如顯示瀏覽器的右鍵菜單）。

### 使用方法
要使用 `oncontextmenu`，你可以將其作為 HTML 元素的屬性，或在 JavaScript 中通過事件監聽器進行綁定。

#### HTML 示例
```html
<div oncontextmenu="return false;">右鍵點擊我</div>
```

#### JavaScript 示例
```javascript
const element = document.getElementById('myElement');
element.addEventListener('contextmenu', function(event) {
    event.preventDefault(); // 禁用默認右鍵菜單
    // 在這裡添加自定義菜單的顯示邏輯
});
```

## 示例
### 基本使用示例
#### 禁用默認右鍵菜單
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>禁用右鍵菜單</title>
    <script>
        function disableContextMenu(event) {
            event.preventDefault();
            alert("右鍵菜單已禁用");
        }
    </script>
</head>
<body>
    <div oncontextmenu="disableContextMenu(event)">右鍵點擊我以禁用菜單</div>
</body>
</html>
```

#### 顯示自定義上下文菜單
```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>自定義上下文菜單</title>
    <style>
        #customMenu {
            display: none;
            position: absolute;
            background: #fff;
            border: 1px solid #ccc;
            padding: 10px;
        }
    </style>
    <script>
        function showCustomMenu(event) {
            event.preventDefault();
            const menu = document.getElementById('customMenu');
            menu.style.display = 'block';
            menu.style.left = `${event.pageX}px`;
            menu.style.top = `${event.pageY}px`;
        }

        function hideCustomMenu() {
            document.getElementById('customMenu').style.display = 'none';
        }
        
        window.addEventListener('click', hideCustomMenu);
    </script>
</head>
<body>
    <div oncontextmenu="showCustomMenu(event)">右鍵點擊我以顯示自定義菜單</div>
    <div id="customMenu">自定義菜單內容</div>
</body>
</html>
```

## 解釋
### 常見問題與注意事項
- **默認行為**：調用 `event.preventDefault()` 是阻止瀏覽器顯示默認右鍵菜單的關鍵步驟。
- **事件傳遞**：`oncontextmenu` 事件會冒泡，因此如果不想讓父元素的事件處理器觸發，需在事件處理完後使用 `event.stopPropagation()`。
- **可訪問性**：考慮對於使用鍵盤的用戶，應提供可訪問的選項，因為右鍵菜單的使用不僅限於滑鼠。
- **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持此事件，但在不同的瀏覽器和版本中，行為可能會有所不同。

## 一句總結
`oncontextmenu` 事件允許開發者在用戶右鍵點擊時自定義行為，從而提供更靈活的互動體驗。