<!--
Meta Description: # SVGAnimatedLengthList 在 JavaScript 中的應用 ## 簡介 SVGAnimatedLengthList 是一個在 SVG（可縮放矢量圖形）中使用的屬性，專門用於表示一系列長度值，這些值可以隨時間變化或動畫化。在 JavaScript 中，開發者可以操作這些長度列表...
Meta Keywords: svganimatedlengthlist, svg, baseval, lengthlist, javascript
-->

# SVGAnimatedLengthList 在 JavaScript 中的應用

## 簡介
SVGAnimatedLengthList 是一個在 SVG（可縮放矢量圖形）中使用的屬性，專門用於表示一系列長度值，這些值可以隨時間變化或動畫化。在 JavaScript 中，開發者可以操作這些長度列表，從而創建動態和互動的圖形效果。

## 文檔
SVGAnimatedLengthList 提供了一個接口來操作 SVG 元素中的長度列表屬性。這些屬性通常用於描述形狀和路徑的尺寸，比如線條、圓形和多邊形的邊界。SVGAnimatedLengthList 包含兩個主要的屬性：baseVal 和 animVal。

- **baseVal**：這是 SVGAnimatedLengthList 的基本值，表示當前長度列表的靜態狀態。
- **animVal**：這是動畫後的值，通常在動畫進行時變化。

### 用法
要使用 SVGAnimatedLengthList，開發者需要訪問相應的 SVG 元素，然後操作它的長度屬性。例如，可以透過 JavaScript 來讀取和修改 baseVal 和 animVal。

```javascript
const svgElement = document.querySelector('svgElement');
const lengthList = svgElement.someLengthListProperty; // 例如：points、stroke-dasharray
console.log(lengthList.baseVal); // 獲取靜態長度列表
```

## 範例
以下是使用 SVGAnimatedLengthList 的基本範例：

```html
<svg width="200" height="200">
  <polyline id="myLine" points="0,0 50,50 100,0" stroke="black" fill="none"/>
</svg>

<script>
  const polyline = document.getElementById('myLine');
  const lengthList = polyline.points;

  // 輸出初始的 points
  console.log(lengthList.baseVal);

  // 修改 points
  lengthList.appendItem(new DOMPoint(150, 150));
  console.log(lengthList.baseVal);
</script>
```

## 解釋
在使用 SVGAnimatedLengthList 時，開發者需要注意以下幾點：

1. **動畫兼容性**：不是所有的 SVG 屬性都支持動畫，因此在使用 SVGAnimatedLengthList 時，必須確認該屬性是否支持動畫。
2. **修改限制**：在某些情況下，對長度列表的修改可能不會立即反映在動畫中，開發者需要了解何時觸發渲染更新。
3. **性能考量**：頻繁修改長度列表可能會影響性能，特別是在大型 SVG 圖形中，應謹慎使用。

## 一句總結
SVGAnimatedLengthList 是一個強大的工具，可在 JavaScript 中動態操作 SVG 元素的長度列表，增強圖形的互動性和動態效果。