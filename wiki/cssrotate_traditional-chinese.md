<!--
Meta Description: # CSSRotate：JavaScript 中的 CSS 旋轉效果 ## 簡介 CSSRotate 是一個用於在 JavaScript 中實現 CSS 旋轉效果的功能，讓開發者能夠輕鬆地創建動態的旋轉動畫，增強用戶界面的交互性和美觀性。 ## 文檔 ### 目的 CSSRotate 主要用於為 H...
Meta Keywords: css, cssrotate, javascript, element, transform
-->

# CSSRotate：JavaScript 中的 CSS 旋轉效果

## 簡介
CSSRotate 是一個用於在 JavaScript 中實現 CSS 旋轉效果的功能，讓開發者能夠輕鬆地創建動態的旋轉動畫，增強用戶界面的交互性和美觀性。

## 文檔
### 目的
CSSRotate 主要用於為 HTML 元素添加旋轉效果，這可以通過 CSS 轉換來實現。它為開發者提供了一種簡單的方法來為網頁元素添加視覺效果，從而提升用戶體驗。

### 使用方法
要使用 CSSRotate，首先需要將 CSS 轉換屬性應用到目標元素上。接著，透過 JavaScript 來改變這些屬性，以達到旋轉的效果。

#### 基本語法：
```css
.element {
    transition: transform 0.5s ease;
}
```

```javascript
function rotateElement(element, degrees) {
    element.style.transform = `rotate(${degrees}deg)`;
}
```

### 詳細信息
- `transform` 屬性是 CSS 中用來應用 2D 或 3D 轉換的屬性。
- `rotate(deg)` 函數用於旋轉元素，`deg` 是旋轉的角度（例如：90deg, 180deg）。
- `transition` 屬性可以讓旋轉效果變得平滑。

## 範例
以下是使用 CSSRotate 的基本範例：

### HTML
```html
<div id="myElement" class="element">旋轉我</div>
<button onclick="rotateElement(document.getElementById('myElement'), 90)">旋轉 90 度</button>
<button onclick="rotateElement(document.getElementById('myElement'), 180)">旋轉 180 度</button>
```

### CSS
```css
.element {
    width: 100px;
    height: 100px;
    background-color: blue;
    transition: transform 0.5s ease;
}
```

### JavaScript
```javascript
function rotateElement(element, degrees) {
    element.style.transform = `rotate(${degrees}deg)`;
}
```

## 解釋
在使用 CSSRotate 時，開發者需注意以下幾點：
1. **初始狀態**：在應用旋轉效果之前，確保元素的初始狀態設置正確，避免出現意外的效果。
2. **多次旋轉**：若多次應用旋轉，可能需要考慮元素的當前旋轉角度，以避免累加旋轉。
3. **性能影響**：在大量元素上使用旋轉效果可能會影響頁面性能，建議適度使用。

## 一句總結
CSSRotate 讓 JavaScript 開發者能夠輕鬆實現元素的旋轉動畫，增強網頁的交互性和吸引力。