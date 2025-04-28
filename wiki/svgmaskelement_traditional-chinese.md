<!--
Meta Description: # SVGMaskElement：JavaScript 中的 SVG 面具元素 ## 概述 `SVGMaskElement` 是一個用於在 SVG（可縮放向量圖形）中創建遮罩的元素，讓用戶能夠定義哪些部分的圖形應該被顯示或隱藏。它通常與其他圖形元素結合使用，以創造豐富的視覺效果。 ## 文件說明 `...
Meta Keywords: svg, mask, svgmaskelement, width, height
-->

# SVGMaskElement：JavaScript 中的 SVG 面具元素

## 概述
`SVGMaskElement` 是一個用於在 SVG（可縮放向量圖形）中創建遮罩的元素，讓用戶能夠定義哪些部分的圖形應該被顯示或隱藏。它通常與其他圖形元素結合使用，以創造豐富的視覺效果。

## 文件說明
`SVGMaskElement` 主要用於控制 SVG 圖形的可見性，透過遮罩技術，允許開發者創建複雜的視覺效果。使用遮罩可以隱藏或顯示圖形的特定部分，並能夠動態地與 JavaScript 進行交互。

### 目的
透過使用 `SVGMaskElement`，開發者能夠：
- 創建自定義的遮罩效果。
- 增強圖形的視覺表現。
- 動態控制圖形的顯示狀態。

### 使用方式
要使用 `SVGMaskElement`，開發者需要在 SVG 文檔中定義一個 `<mask>` 元素，並將其應用到其他圖形元素上。以下是基本的使用方式：

```xml
<svg width="200" height="200">
  <defs>
    <mask id="myMask">
      <rect width="100%" height="100%" fill="white"/>
      <circle cx="100" cy="100" r="50" fill="black"/>
    </mask>
  </defs>
  
  <rect x="0" y="0" width="200" height="200" fill="red" mask="url(#myMask)"/>
</svg>
```

在這個例子中，紅色矩形的中心部分被黑色圓形遮罩隱藏，最終的顯示效果只會顯示紅色矩形的外圍。

## 範例
### 基本用法示例
```xml
<svg width="300" height="300">
  <defs>
    <mask id="mask1">
      <rect width="100%" height="100%" fill="white"/>
      <circle cx="150" cy="150" r="50" fill="black"/>
    </mask>
  </defs>
  
  <rect width="300" height="300" fill="blue" mask="url(#mask1)"/>
</svg>
```
在這個範例中，整個藍色矩形的中心部分會被遮罩，顯示出底部的白色。

### 動態控制
使用 JavaScript，可以動態地改變遮罩的屬性，例如：

```javascript
const mask = document.getElementById('mask1');
const circle = mask.querySelector('circle');

circle.setAttribute('r', '80'); // 動態改變圓形的半徑
```

## 解釋
使用 `SVGMaskElement` 時，開發者應注意以下幾點：
- 遮罩的顏色：白色表示可見，黑色表示隱藏，其他顏色會產生不同程度的透明效果。
- 遮罩的範圍：遮罩的大小和形狀必須符合應用它的圖形元素，否則可能無法正確顯示。
- 支援性：並非所有瀏覽器都完全支援 SVG 遮罩，建議在使用前進行瀏覽器兼容性測試。

## 總結
`SVGMaskElement` 提供了一種強大的方式來控制 SVG 圖形的顯示效果，透過遮罩技術，開發者可以輕鬆地實現各種視覺效果。