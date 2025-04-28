<!--
Meta Description: # CSS動畫 (CSSAnimation) 與 JavaScript 的關係 ## 簡介 CSS動畫 (CSSAnimation) 是一種使用 CSS 和 JavaScript 來創建動態效果的技術。它能夠讓網頁元素以流暢的方式過渡，增強用戶體驗。 ## 文件說明 CSS動畫的主要目的是使網頁元素...
Meta Keywords: javascript, element, css, animation, keyframes
-->

# CSS動畫 (CSSAnimation) 與 JavaScript 的關係

## 簡介
CSS動畫 (CSSAnimation) 是一種使用 CSS 和 JavaScript 來創建動態效果的技術。它能夠讓網頁元素以流暢的方式過渡，增強用戶體驗。

## 文件說明
CSS動畫的主要目的是使網頁元素能夠隨時間變化其樣式。這可以通過定義關鍵幀 (keyframes) 和動畫屬性來實現。JavaScript 可以用來控制這些動畫的開始、暫停和結束，增強了使用者與網頁的互動性。

### 用法
CSS動畫可以通過以下步驟來使用：
1. **定義關鍵幀**：使用 `@keyframes` 來定義動畫的不同階段。
2. **應用動畫屬性**：使用 CSS 的 `animation` 屬性來指定動畫的持續時間、延遲、次數等。
3. **使用 JavaScript 控制動畫**：可以使用 JavaScript 來動態地啟動或停止動畫。

### 詳細資訊
- **關鍵幀定義**：
    ```css
    @keyframes example {
        0% {background-color: red;}
        100% {background-color: yellow;}
    }
    ```
- **應用動畫屬性**：
    ```css
    .animated-element {
        animation-name: example;
        animation-duration: 4s;
        animation-fill-mode: forwards;
    }
    ```
- **JavaScript 控制動畫**：
    ```javascript
    const element = document.querySelector('.animated-element');
    element.style.animationPlayState = 'paused'; // 暫停動畫
    element.style.animationPlayState = 'running'; // 開始動畫
    ```

## 範例
### 基本用法範例
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        @keyframes slide {
            0% {transform: translateX(0);}
            100% {transform: translateX(100px);}
        }
        .slide-element {
            width: 100px;
            height: 100px;
            background-color: blue;
            animation: slide 2s infinite alternate;
        }
    </style>
</head>
<body>
    <div class="slide-element"></div>
</body>
</html>
```

## 解釋
在使用 CSS動畫時，常見的問題包括：
- **動畫不啟動**：確保 CSS 和 JavaScript 正確連接，並檢查屬性名稱是否拼寫正確。
- **不支持的瀏覽器**：部分舊版瀏覽器可能不支持 CSS動畫，需檢查相容性。
- **性能問題**：過多的動畫或不當使用可能會影響頁面性能，應謹慎使用。

## 一句總結
CSS動畫結合 JavaScript 是提升網頁互動性和用戶體驗的一個強大工具。