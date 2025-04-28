<!--
Meta Description: # SVGAnimatedNumberList：JavaScript中的可動畫數字列表 ## 概述 `SVGAnimatedNumberList` 是 SVG（可縮放向量圖形）中用於表示一組可動畫數字的對象，通常用於動態改變 SVG 元素的屬性值。它在 JavaScript 中的應用使開發者能夠控制...
Meta Keywords: svganimatednumberlist, svg, baseval, circle, strokedasharray
-->

# SVGAnimatedNumberList：JavaScript中的可動畫數字列表

## 概述
`SVGAnimatedNumberList` 是 SVG（可縮放向量圖形）中用於表示一組可動畫數字的對象，通常用於動態改變 SVG 元素的屬性值。它在 JavaScript 中的應用使開發者能夠控制動畫效果，提升圖形的互動性。

## 文檔
`SVGAnimatedNumberList` 主要用於 SVG 圖形的動畫效果，它包含兩個屬性：

1. **baseVal**：表示列表的基本值，類型為 `SVGNumberList`。
2. **animVal**：表示動畫後的值，類型為 `SVGNumberList`。

### 使用方法
`SVGAnimatedNumberList` 通常在 SVG 元素的屬性中使用，如 `stroke-dasharray` 或 `viewBox`，以便實現動畫效果。以下是如何使用 `SVGAnimatedNumberList` 的基本步驟：

1. 獲取 SVG 元素。
2. 訪問其 `animated` 屬性。
3. 動態修改 `baseVal`，以達到動畫效果。

### 詳細說明
- `SVGNumberList` 是一組數字，可以包含零或多個 `SVGNumber`。
- `baseVal` 和 `animVal` 的值可以是不同的，這使得開發者可以在不影響基本值的情況下進行動畫。
- 要設置 `baseVal`，可使用 `appendItem()` 或 `replaceItem()` 方法來添加或替代數字。

## 範例
以下是一個簡單的範例，展示如何使用 `SVGAnimatedNumberList` 來實現動畫效果：

```html
<svg width="200" height="200">
    <circle id="myCircle" cx="100" cy="100" r="40" stroke="black" stroke-width="2" fill="red"/>
</svg>

<script>
    const circle = document.getElementById('myCircle');
    const strokeDashArray = circle.style.strokeDasharray;

    // 使用 SVGAnimatedNumberList 動態改變 strokeDasharray
    circle.style.strokeDasharray = "10, 5";

    // 動畫效果
    setTimeout(() => {
        circle.style.strokeDasharray = "20, 10";
    }, 1000);
</script>
```

## 解釋
在使用 `SVGAnimatedNumberList` 時，開發者需注意以下幾點：

- 確保所使用的 SVG 元素支持 `SVGAnimatedNumberList`。
- 注意 `baseVal` 和 `animVal` 的不同，特別是在動畫過程中，這可能會導致預期之外的效果。
- 在進行動畫時，考慮性能問題，特別是在高幀率動畫中，需確保不會造成卡頓。

## 一句話總結
`SVGAnimatedNumberList` 是一個強大的工具，用於在 JavaScript 中創建動態的 SVG 數字動畫效果。