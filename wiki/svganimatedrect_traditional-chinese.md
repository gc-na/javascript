<!--
Meta Description: # SVGAnimatedRect：JavaScript 中的 SVG 動畫矩形屬性 ## 摘要 `SVGAnimatedRect` 是一個用於描述可動畫的矩形的 SVG 屬性，允許開發者在 JavaScript 中動態操控 SVG 矩形的形狀和位置，從而實現豐富的動畫效果。 ## 文檔 `SVGA...
Meta Keywords: svg, rect, svganimatedrect, width, javascript
-->

# SVGAnimatedRect：JavaScript 中的 SVG 動畫矩形屬性

## 摘要
`SVGAnimatedRect` 是一個用於描述可動畫的矩形的 SVG 屬性，允許開發者在 JavaScript 中動態操控 SVG 矩形的形狀和位置，從而實現豐富的動畫效果。

## 文檔
`SVGAnimatedRect` 是 SVG 2 中的一個接口，用於表示一個矩形的動畫屬性。它包含三個主要的屬性：`baseVal`、`animVal` 和 `rect`，可以用來對矩形的寬度、高度、x 和 y 位移進行動畫處理。

### 目的
`SVGAnimatedRect` 的主要目的是允許開發者創建可動畫的 SVG 矩形，從而增強用戶界面的互動性和視覺吸引力。

### 用法
在 JavaScript 中，開發者可以通過訪問 SVG 元素的 `getBBox()` 方法來獲取矩形的當前邊界框，並使用 `baseVal` 和 `animVal` 來設置和獲取矩形的動畫屬性。

### 詳細信息
- **屬性**:
  - `baseVal`：表示矩形的基本值。
  - `animVal`：表示矩形的當前動畫值，通常在動畫進行中會改變。
  
- **方法**:
  - 可以通過 `setAttribute()` 和 `getAttribute()` 方法來設置和獲取矩形的屬性。
  
- **使用情境**:
  - 適合用於創建過渡動畫、視覺效果和動態數據可視化。

## 範例
### 基本使用範例
```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="50" fill="blue" />
</svg>

<script>
  const rect = document.getElementById('myRect');
  rect.setAttribute('x', '50');  // 更改矩形的 x 坐標
  rect.setAttribute('width', '150');  // 更改矩形的寬度
</script>
```

### 動畫範例
```html
<svg width="200" height="200">
  <rect id="animatedRect" x="10" y="10" width="100" height="50" fill="red">
    <animate attributeName="x" from="10" to="150" dur="2s" fill="freeze" />
  </rect>
</svg>
```

## 解釋
在使用 `SVGAnimatedRect` 時，開發者需要注意以下幾點：
- 動畫的持續時間 (`dur`) 必須設定妥當，否則動畫可能不會如預期運行。
- 使用 `fill="freeze"` 可以使動畫在結束後保持在最後狀態。
- 在使用 `getAttribute()` 和 `setAttribute()` 時，必須確保指定的屬性名稱正確無誤，否則將無法成功獲取或設定值。

## 一行總結
`SVGAnimatedRect` 允許開發者在 JavaScript 中動態操控 SVG 矩形的動畫效果，增強用戶互動體驗。