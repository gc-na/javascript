<!--
Meta Description: # SVGAnimatedLengthList：在 JavaScript 中使用的 SVG 動畫長度列表 ## 簡介 `SVGAnimatedLengthList` 是一個在 SVG（可縮放向量圖形）中使用的接口，用於表示動畫長度列表。它提供了一種方法來操控和獲取與 SVG 元素相關的長度數據，並支...
Meta Keywords: svg, svganimatedlengthlist, javascript, let, baseval
-->

# SVGAnimatedLengthList：在 JavaScript 中使用的 SVG 動畫長度列表

## 簡介
`SVGAnimatedLengthList` 是一個在 SVG（可縮放向量圖形）中使用的接口，用於表示動畫長度列表。它提供了一種方法來操控和獲取與 SVG 元素相關的長度數據，並支持動畫效果。

## 文檔
### 目的
`SVGAnimatedLengthList` 的目的是提供對 SVG 元素的長度屬性的動畫控制。這些屬性可以包括寬度、高度、半徑等，並且隨著時間變化而變化。它的主要用途是在 SVG 動畫中提供更靈活的長度處理。

### 使用方法
在 JavaScript 中，您可以通過 SVG 元素的屬性來訪問 `SVGAnimatedLengthList`。通常用法如下：

```javascript
let svgElement = document.getElementById('yourSvgElement');
let animatedLengthList = svgElement.someLengthListProperty; // 例如: animatedRadius
```

`SVGAnimatedLengthList` 主要包含以下屬性：
- `baseVal`：返回一個 `SVGLengthList` 對象，表示基礎長度列表。
- `animVal`：返回一個 `SVGLengthList` 對象，表示當前動畫長度列表。

### 詳細資訊
`SVGAnimatedLengthList` 是用於表示一組長度的數據結構，通常在 SVG 動畫或動態變化中使用。其本質上是由一系列 `SVGLength` 物件組成，這些物件可以指定不同的單位（例如，像素、百分比等）。它的設計使得開發者能夠輕鬆地對長度進行動畫處理。

## 範例
以下是一個簡單的範例，展示如何使用 `SVGAnimatedLengthList`：

```html
<svg width="100" height="100">
  <circle id="myCircle" cx="50" cy="50" r="20" fill="red" />
</svg>

<script>
  let circle = document.getElementById('myCircle');
  let radiusList = circle.r; // 獲取動畫半徑列表

  console.log(radiusList.baseVal.value); // 輸出當前半徑值
  radiusList.baseVal.value = 30; // 改變半徑
</script>
```

這段代碼中，我們創建了一個紅色的圓形，然後通過 JavaScript 獲取並修改其半徑屬性。

## 解釋
在使用 `SVGAnimatedLengthList` 時，有幾個常見的問題和注意事項：
- 確保 SVG 元素已經正確加載，否則可能無法正確訪問其屬性。
- 如果在動畫期間獲取 `animVal`，請注意它可能與 `baseVal` 不同，因為 `animVal` 表示正在進行的動畫狀態。
- 在設置長度時，必須確保所用的單位正確，否則可能會導致意想不到的顯示效果。

## 一句總結
`SVGAnimatedLengthList` 允許開發者在 SVG 中有效地控制和操作動畫長度列表。