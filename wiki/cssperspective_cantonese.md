<!--
Meta Description: # CSSPerspective：JavaScript 中的 CSS 透視效果 ## 簡介 CSSPerspective 是一個用於創造 3D 透視效果的 CSS 屬性，當與 JavaScript 結合使用時，可以為網頁元素添加深度和立體感，增強用戶體驗。 ## 文檔 ### 目的 CSSPersp...
Meta Keywords: cssperspective, javascript, css, transform, perspective
-->

# CSSPerspective：JavaScript 中的 CSS 透視效果

## 簡介
CSSPerspective 是一個用於創造 3D 透視效果的 CSS 屬性，當與 JavaScript 結合使用時，可以為網頁元素添加深度和立體感，增強用戶體驗。

## 文檔
### 目的
CSSPerspective 屬性定義了 3D 空間中的觀察者與 Z 軸的距離，這會影響子元素的 3D 效果。使用 JavaScript 可以動態改變這個屬性，從而實現更加生動的視覺效果。

### 使用方法
CSSPerspective 通常與 CSS 的 `transform` 屬性一起使用。你可以在 CSS 中定義 `perspective`，然後在 JavaScript 中通過修改這個屬性來實現動態效果。

#### 語法
```css
.parent {
    perspective: <length>;
}
```

### 詳細信息
- `<length>`: 定義透視的距離，通常以像素（px）表示。值越小，透視效果越強烈。
- 透視屬性應該應用於容器元素，而不是直接應用於子元素。

## 範例
### 基本用法
以下示例展示了如何在 CSS 中設置透視效果，並使用 JavaScript 動態改變它：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            perspective: 800px;
            width: 300px;
            height: 300px;
            position: relative;
        }

        .box {
            width: 100%;
            height: 100%;
            background: red;
            transform: rotateY(45deg);
            transition: transform 0.5s;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box"></div>
    </div>

    <script>
        document.querySelector('.container').addEventListener('click', function() {
            this.style.perspective = '1000px'; // 動態改變透視距離
        });
    </script>
</body>
</html>
```

## 解釋
- **常見問題**: 使用 CSSPerspective 時，可能會發現子元素的變形效果不如預期，這通常是因為透視屬性沒有正確應用於容器元素。
- **陷阱**: 如果透視距離設置得過小，可能會導致不自然的 3D 效果。建議在使用時進行多次測試，以確保視覺效果符合預期。
- **其他注意事項**: 在 3D 效果中，子元素的 `transform-style` 屬性應設置為 `preserve-3d`，以確保 3D 效果的正確顯示。

## 一句總結
CSSPerspective 是一個強大的工具，可以與 JavaScript 結合使用，為網頁元素創造生動的 3D 透視效果。