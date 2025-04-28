<!--
Meta Description: # SVGAnimatedPreserveAspectRatio：JavaScript 中的 SVG 動畫比例保持屬性 ## 概述 `SVGAnimatedPreserveAspectRatio` 是一個用於 SVG（可縮放向量圖形）的屬性，允許開發者控制如何在不同的顯示區域中保留圖形的比例。這對於...
Meta Keywords: baseval, svg, svganimatedpreserveaspectratio, preserveaspectratio, svgelement
-->

# SVGAnimatedPreserveAspectRatio：JavaScript 中的 SVG 動畫比例保持屬性

## 概述
`SVGAnimatedPreserveAspectRatio` 是一個用於 SVG（可縮放向量圖形）的屬性，允許開發者控制如何在不同的顯示區域中保留圖形的比例。這對於確保圖形在縮放或調整大小時不會失真非常重要。

## 文檔
`SVGAnimatedPreserveAspectRatio` 是一個動畫屬性，主要用於描述如何調整 SVG 圖形以適應其顯示容器。這個屬性包含兩個部分：`baseVal` 和 `animVal`。`baseVal` 是該屬性的當前值，而 `animVal` 則是正在進行動畫的值。

### 使用目的
- 確保 SVG 圖形在不同大小顯示時保持其視覺比例。
- 允許動畫過程中動態改變 SVG 的顯示方式。

### 使用方法
在 JavaScript 中，可以透過以下方式來訪問和修改 `SVGAnimatedPreserveAspectRatio` 的屬性：

```javascript
let svgElement = document.getElementById("mySvg");
let preserveAspectRatio = svgElement.preserveAspectRatio;

// 獲取當前的 baseVal
console.log(preserveAspectRatio.baseVal);

// 設置新的 baseVal
preserveAspectRatio.baseVal = "xMidYMid meet";
```

## 示例
以下是一個簡單的範例，展示如何使用 `SVGAnimatedPreserveAspectRatio`：

```html
<svg id="mySvg" width="200" height="200" viewBox="0 0 100 100">
    <rect width="100" height="100" fill="blue" />
</svg>

<script>
    let svgElement = document.getElementById("mySvg");
    console.log(svgElement.preserveAspectRatio.baseVal); // 輸出當前的 baseVal
    svgElement.preserveAspectRatio.baseVal = "xMidYMid meet"; // 設置新的 baseVal
</script>
```

## 解釋
使用 `SVGAnimatedPreserveAspectRatio` 時，開發者需要注意以下幾點：
- 在某些情況下，所選的 `preserveAspectRatio` 值可能會導致內容的裁剪或變形，因此必須仔細選擇。
- 確保在 SVG 元素加載完畢後再調用此屬性，否則可能會獲取到未正確初始化的值。

## 一句總結
`SVGAnimatedPreserveAspectRatio` 是一個強大的工具，用於控制 SVG 圖形在不同顯示環境下的比例保持行為。