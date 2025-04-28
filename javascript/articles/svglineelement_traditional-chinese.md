<!--
Meta Description: # SVGLineElement：JavaScript 中的 SVG 線元素 ## 簡介 SVGLineElement 是一種在 Scalable Vector Graphics (SVG) 中表示線的元素，並可通過 JavaScript 進行操控。這個元素允許開發者在網頁中繪製直線，並可以與其他 ...
Meta Keywords: svg, svglineelement, stroke, 200, line
-->

# SVGLineElement：JavaScript 中的 SVG 線元素

## 簡介
SVGLineElement 是一種在 Scalable Vector Graphics (SVG) 中表示線的元素，並可通過 JavaScript 進行操控。這個元素允許開發者在網頁中繪製直線，並可以與其他 SVG 元素結合使用來創建更複雜的圖形。

## 文檔
### 目的
SVGLineElement 主要用於創建和操作 SVG 圖形中的直線。這種元素不僅能夠定義線的起點和終點，還可以設置樣式屬性，如顏色和寬度。

### 使用方式
SVGLineElement 是通過 SVG 的 `<line>` 標籤來創建的，可以使用 JavaScript 來動態設置其屬性。以下是關鍵屬性：

- `x1`：起點的 x 坐標。
- `y1`：起點的 y 坐標。
- `x2`：終點的 x 坐標。
- `y2`：終點的 y 坐標。
- `stroke`：線的顏色。
- `stroke-width`：線的寬度。

### 詳細說明
要使用 SVGLineElement，首先需在 HTML 中定義一個 SVG 標籤，然後在其中加入 `<line>` 標籤。可以使用 JavaScript 來動態訪問和修改線的屬性，從而實現交互效果。

```html
<svg width="200" height="200">
  <line id="myLine" x1="0" y1="0" x2="200" y2="200" stroke="black" stroke-width="2" />
</svg>
```

## 範例
以下是在 JavaScript 中使用 SVGLineElement 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>SVGLineElement 範例</title>
</head>
<body>
    <svg width="200" height="200">
        <line id="myLine" x1="0" y1="0" x2="200" y2="200" stroke="black" stroke-width="2" />
    </svg>
    <script>
        // 修改線條的顏色和寬度
        const line = document.getElementById('myLine');
        line.setAttribute('stroke', 'red');
        line.setAttribute('stroke-width', '5');
    </script>
</body>
</html>
```

## 解釋
在使用 SVGLineElement 時，有幾個常見的陷阱需要注意：

1. **坐標系統**：SVG 的坐標系統與 HTML 的坐標系統不同，注意線的坐標必須在 SVG 的範圍內。
2. **屬性更新**：在 JavaScript 中動態更新屬性時，必須使用 `setAttribute` 方法。
3. **樣式影響**：CSS 樣式可能會影響 SVG 元素的顯示，確保樣式不會遮蓋或改變線的外觀。

## 總結
SVGLineElement 是一個強大的工具，用於在網頁中創建和操作線條，為網頁增添了豐富的視覺效果。