<!--
Meta Description: # JavaScript 中的焦點 (Focus) 特性 ## 概述 在 JavaScript 中，"焦點" 是指用戶界面中可以接受輸入的元素（例如文本框、按鈕等）當前的活動狀態。透過管理焦點，開發者可以改善用戶體驗，使得用戶更容易與應用程序交互。 ## 文檔 ### 目的 焦點的主要目的在於使某個...
Meta Keywords: focus, html, javascript, button, input
-->

# JavaScript 中的焦點 (Focus) 特性

## 概述
在 JavaScript 中，"焦點" 是指用戶界面中可以接受輸入的元素（例如文本框、按鈕等）當前的活動狀態。透過管理焦點，開發者可以改善用戶體驗，使得用戶更容易與應用程序交互。

## 文檔
### 目的
焦點的主要目的在於使某個元素成為用戶輸入的目標。這對於表單元素特別重要，因為用戶可以輕鬆地輸入數據而不需要用鼠標點擊。

### 使用
在 JavaScript 中，可以使用 `focus()` 方法來設置焦點到特定的 HTML 元素。這個方法通常用於表單元素，當用戶加載頁面或在特定事件發生時自動設置焦點。

### 詳細說明
- **語法**: `element.focus()`
- **參數**: 無
- **返回值**: 無
- **適用元素**: `input`, `textarea`, `button`, `select` 等可互動的元素。

## 示例
### 基本用法
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>焦點示例</title>
</head>
<body>
    <input type="text" id="myInput" placeholder="請輸入文本">
    <button id="focusButton">設置焦點</button>

    <script>
        document.getElementById('focusButton').onclick = function() {
            document.getElementById('myInput').focus();
        }
    </script>
</body>
</html>
```
在此示例中，當用戶按下“設置焦點”按鈕時，文本框將獲得焦點。

## 解釋
### 常見陷阱
1. **自動焦點問題**: 在頁面加載時自動設置焦點可能會影響用戶體驗，特別是在屏幕閱讀器使用者中。建議在合適的時候再設置焦點。
2. **焦點連鎖**: 如果在一個事件中設置多個元素的焦點，可能會導致不必要的焦點變化，影響用戶體驗。
3. **CSS 樣式影響**: 確保使用 CSS 使得獲得焦點的元素明顯可見，這樣用戶才能知道哪個元素是活動的。

## 總結
JavaScript 的焦點管理是提升用戶互動的重要工具，透過簡單的 `focus()` 方法，開發者可以輕鬆地控制用戶界面的輸入焦點。