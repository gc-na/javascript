<!--
Meta Description: # SVGFEDisplacementMapElement：JavaScript 中的 SVG 位移映射元素 ## 簡介 SVGFEDisplacementMapElement 是一個用於 SVG（可縮放向量圖形）的元素，主要用來對圖形進行位移映射，這在圖像處理和視覺效果中非常有用。透過 JavaS...
Meta Keywords: svg, svgfedisplacementmapelement, javascript, filter, displacementmap
-->

# SVGFEDisplacementMapElement：JavaScript 中的 SVG 位移映射元素

## 簡介
SVGFEDisplacementMapElement 是一個用於 SVG（可縮放向量圖形）的元素，主要用來對圖形進行位移映射，這在圖像處理和視覺效果中非常有用。透過 JavaScript，開發者可以動態操控這個元素以實現複雜的視覺效果。

## 文檔
### 目的
SVGFEDisplacementMapElement 的主要目的是利用位移映射來創造視覺效果，特別是在圖像的變形和扭曲方面。這個元素通常與其他 SVG 元素如 `<filter>` 一起使用，以達到更複雜的效果。

### 用法
SVGFEDisplacementMapElement 是 SVG 濾鏡的一部分，通常用於 `<filter>` 標籤內。開發者可以在 JavaScript 中創建這個元素並設置其屬性來控制效果。例如，`in` 和 `in2` 屬性用於指定源和位移圖像，`scale` 屬性則控制位移的強度。

#### 屬性
- **in**：指定要進行位移映射的源圖像。
- **in2**：指定用作位移圖像的第二個圖像。
- **scale**：定義位移的強度，可以是正數或負數。

### 實例
以下是如何在 JavaScript 中使用 SVGFEDisplacementMapElement 的基本示例：

```javascript
// 創建 SVG 濾鏡
const svgNS = "http://www.w3.org/2000/svg";
let filter = document.createElementNS(svgNS, "filter");

// 創建位移映射元素
let displacementMap = document.createElementNS(svgNS, "feDisplacementMap");
displacementMap.setAttribute("in", "SourceGraphic");
displacementMap.setAttribute("in2", "displacementImage");
displacementMap.setAttribute("scale", "20");

// 將位移映射元素添加到濾鏡中
filter.appendChild(displacementMap);

// 將濾鏡添加到 SVG 中
let svgElement = document.querySelector("svg");
svgElement.appendChild(filter);
```

### 解釋
使用 SVGFEDisplacementMapElement 時，開發者需要留意以下幾點：
- 確保 `in` 和 `in2` 屬性正確設置，否則效果將無法顯示。
- `scale` 屬性應謹慎設置，過高的值可能導致過度失真。
- 在使用 JavaScript 動態創建 SVG 元素時，需確保正確的命名空間。

## 一行總結
SVGFEDisplacementMapElement 是一個強大的 SVG 元素，用於在 JavaScript 中生成動態的位移映射效果。