<!--
Meta Description: # CSS 動畫 (CSS Animation) 與 JavaScript 的關聯 ## 概述 CSS 動畫是一種利用 CSS 定義的技術，能夠為網頁元素創建流暢的視覺效果。透過 JavaScript，可以更動態地控制 CSS 動畫，增強用戶體驗。 ## 文檔 ### 目的 CSS 動畫通常用於改善...
Meta Keywords: css, javascript, animation, myelement, html
-->

# CSS 動畫 (CSS Animation) 與 JavaScript 的關聯

## 概述
CSS 動畫是一種利用 CSS 定義的技術，能夠為網頁元素創建流暢的視覺效果。透過 JavaScript，可以更動態地控制 CSS 動畫，增強用戶體驗。

## 文檔

### 目的
CSS 動畫通常用於改善網頁的視覺吸引力，增加互動性。結合 JavaScript，開發者能夠在特定事件觸發時控制動畫的開始、結束或重複。

### 使用方法
要使用 CSS 動畫，首先需要在 CSS 中定義動畫及其關鍵幀 (keyframes)。然後，透過 JavaScript 可以添加、移除或修改這些樣式。

#### CSS 範例
```css
@keyframes slideIn {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

.animated {
    animation: slideIn 0.5s ease-in-out forwards;
}
```

#### JavaScript 範例
```javascript
document.getElementById('myElement').classList.add('animated');
```

## 範例

### 基本用法
以下為一個簡單的範例，當用戶點擊按鈕時，元素將從左側滑入。

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .fade {
            animation: fadeIn 1s forwards;
        }

        #myElement {
            width: 100px;
            height: 100px;
            background-color: blue;
            display: none;
        }
    </style>
    <title>CSS 動畫範例</title>
</head>
<body>
    <button id="animateBtn">點擊我以顯示元素</button>
    <div id="myElement"></div>

    <script>
        document.getElementById('animateBtn').addEventListener('click', function() {
            const element = document.getElementById('myElement');
            element.style.display = 'block'; // 顯示元素
            element.classList.add('fade'); // 添加動畫
        });
    </script>
</body>
</html>
```

## 解釋

### 常見問題
1. **動畫不顯示：** 確保元素在動畫開始前是可見的，且正確添加了 CSS 類別。
2. **動畫延遲：** 使用 `animation-delay` 屬性可以設置動畫的延遲時間，需注意其與 `setTimeout` 的使用。
3. **CSS 覆蓋：** 確保沒有其他 CSS 規則干擾動畫效果。

### 附加說明
- CSS 動畫性能較好，因為它們通常由瀏覽器的合成層處理。
- 可以使用 JavaScript 的 `Animation` API 獲得更高級的控制，例如播放、暫停和重啟動畫。

## 總結
CSS 動畫結合 JavaScript 可以創建引人入勝的視覺效果，提升用戶互動體驗。