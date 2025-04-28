<!--
Meta Description: # CSSRotate：JavaScript 中的 CSS 旋轉效果 ## 概述 CSSRotate 是一個用於在 JavaScript 中操控 CSS 旋轉效果的功能。透過 CSSRotate，開發者可以輕鬆地為網頁元素添加旋轉動畫，提高用戶介面的互動性和視覺效果。 ## 文檔 ### 目的 CS...
Meta Keywords: cssrotate, css, transform, javascript, html
-->

# CSSRotate：JavaScript 中的 CSS 旋轉效果

## 概述
CSSRotate 是一個用於在 JavaScript 中操控 CSS 旋轉效果的功能。透過 CSSRotate，開發者可以輕鬆地為網頁元素添加旋轉動畫，提高用戶介面的互動性和視覺效果。

## 文檔
### 目的
CSSRotate 主要用於為 HTML 元素添加旋轉效果，這對於增強網站的視覺吸引力非常有用。它可以用於創建炫酷的轉場效果、圖像旋轉展示等。

### 用法
要使用 CSSRotate，開發者通常需要結合 JavaScript 的 DOM 操作和 CSS 的 transform 屬性。以下是基本的用法步驟：

1. **選擇要旋轉的元素**：使用 JavaScript 選擇需要旋轉的 DOM 元素。
2. **設置旋轉角度**：通過改變元素的 CSS 屬性來設置旋轉角度。
3. **觸發旋轉效果**：可以通過事件（如點擊或鼠標懸停）來觸發旋轉效果。

### 詳細說明
CSSRotate 主要依賴於 CSS 的 `transform` 屬性。這個屬性允許我們對元素進行旋轉、縮放、位移等變形操作。旋轉的角度可以是正值（順時針旋轉）或負值（逆時針旋轉）。這裡是一個基本的旋轉方程：

```css
transform: rotate(角度);
```

在 JavaScript 中，我們可以使用以下代碼來應用旋轉效果：

```javascript
const element = document.getElementById('myElement');
element.style.transform = 'rotate(45deg)'; // 順時針旋轉 45 度
```

## 示例
### 基本用法示例
以下是一個簡單的例子，展示如何使用 CSSRotate：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSSRotate 示例</title>
    <style>
        #myElement {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: transform 0.5s; /* 添加過渡效果 */
        }
    </style>
</head>
<body>
    <div id="myElement"></div>
    <button id="rotateButton">旋轉</button>

    <script>
        const element = document.getElementById('myElement');
        const button = document.getElementById('rotateButton');
        
        button.addEventListener('click', () => {
            element.style.transform = 'rotate(45deg)'; // 點擊按鈕後旋轉
        });
    </script>
</body>
</html>
```

在這個例子中，當用戶點擊按鈕時，紅色方塊將會旋轉 45 度。

## 解釋
### 常見陷阱
- **旋轉角度不生效**：如果元素的 `transform` 屬性已經設置，新的旋轉值可能會被覆蓋。確保在應用新旋轉時，考慮到之前的旋轉值。
- **不支持的瀏覽器**：雖然大多數現代瀏覽器都支持 CSS 旋轉，但在某些舊版瀏覽器中可能會有兼容性問題。

### 額外注意事項
- **性能考量**：過多的旋轉效果可能會影響性能，尤其是在移動設備上。使用 CSS 的 `will-change` 屬性可以幫助優化性能。
- **連續旋轉**：如果需要連續旋轉，可以使用 CSS 的動畫（`@keyframes`）來實現。

## 一句總結
CSSRotate 是一個強大的工具，讓開發者可以輕鬆為網頁元素添加旋轉效果，提升用戶體驗。