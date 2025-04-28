<!--
Meta Description: # SVGPreserveAspectRatio：JavaScript 中的 SVG 內容比例保留屬性 ## 概述 SVGPreserveAspectRatio 是一個 SVG（可縮放矢量圖形）屬性，用於控制如何在不同的視口（viewport）中呈現 SVG 內容。透過 JavaScript，可以動...
Meta Keywords: svg, javascript, svgpreserveaspectratio, preserveaspectratio, xmidymid
-->

# SVGPreserveAspectRatio：JavaScript 中的 SVG 內容比例保留屬性

## 概述
SVGPreserveAspectRatio 是一個 SVG（可縮放矢量圖形）屬性，用於控制如何在不同的視口（viewport）中呈現 SVG 內容。透過 JavaScript，可以動態設置這個屬性，以達到更好的視覺效果。

## 文檔
### 目的
SVGPreserveAspectRatio 屬性定義了在縮放或填充 SVG 圖形時，如何保持圖形的寬高比。它對於確保圖形不會因為視口的改變而失真至關重要。

### 使用方法
SVGPreserveAspectRatio 屬性可以在 `<svg>` 標籤中設置，並且可以通過 JavaScript 來更改其值。這個屬性的值包括：

- `none`：不保留比例，隨意填充。
- `xMinYMin`：保留比例，並將圖形對齊到視口的左上角。
- `xMidYMid`：保留比例，並將圖形居中。
- `xMaxYMax`：保留比例，並將圖形對齊到視口的右下角。
- `xMinYMid`、`xMidYMin`、`xMinYMax`、`xMaxYMid` 等：其他對齊選項。

### 詳細說明
在 JavaScript 中，可以通過 DOM 來訪問和設置 SVGPreserveAspectRatio 屬性。以下是如何使用 JavaScript 設定該屬性的一個範例：

```javascript
const svgElement = document.querySelector('svg');
svgElement.setAttribute('preserveAspectRatio', 'xMidYMid meet');
```

這段代碼將 SVG 的 `preserveAspectRatio` 屬性設置為 `xMidYMid meet`，這意味著圖形將保持比例並居中顯示。

## 範例
### 基本使用
```html
<svg width="200" height="200" preserveAspectRatio="xMidYMid meet">
    <rect x="10" y="10" width="180" height="180" fill="blue"/>
</svg>
```

在這個範例中，藍色矩形會在 SVG 視口中保持其比例並居中顯示。

### JavaScript 動態設置
```html
<svg id="mySVG" width="300" height="300">
    <circle cx="150" cy="150" r="100" fill="red"/>
</svg>

<script>
    const svgElement = document.getElementById('mySVG');
    svgElement.setAttribute('preserveAspectRatio', 'xMinYMin slice');
</script>
```

這段代碼在加載後會將 SVG 的 `preserveAspectRatio` 屬性設置為 `xMinYMin slice`，使得圓形在視口的左上角切割顯示。

## 解釋
### 常見陷阱
1. **未設置屬性**：如果不設置 `preserveAspectRatio`，SVG 內容可能會失真。
2. **理解不同的對齊方式**：不熟悉對齊選項可能導致不預期的視覺效果。

### 附加說明
在使用 SVGPreserveAspectRatio 時，確保了解視口的寬高比和 SVG 本身的寬高比之間的差異，以便選擇合適的對齊方式。

## 一句總結
SVGPreserveAspectRatio 是 SVG 中用於控制圖形在視口中顯示比例的重要屬性，並可通過 JavaScript 靈活調整。