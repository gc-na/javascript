<!--
Meta Description: # SVGLinearGradientElement: JavaScript 中的線性漸變元素 ## 簡介 `SVGLinearGradientElement` 是一個用於在 SVG (可縮放矢量圖形) 中創建線性漸變的元素。這個元素可以讓開發者在圖形中應用顏色過渡效果，增強視覺吸引力。 ## 文檔...
Meta Keywords: svg, svglineargradientelement, stop, 200, javascript
-->

# SVGLinearGradientElement: JavaScript 中的線性漸變元素

## 簡介
`SVGLinearGradientElement` 是一個用於在 SVG (可縮放矢量圖形) 中創建線性漸變的元素。這個元素可以讓開發者在圖形中應用顏色過渡效果，增強視覺吸引力。

## 文檔
`SVGLinearGradientElement` 是 `SVGGradientElement` 的一個子類，主要用於定義從一個點到另一個點的顏色過渡。這個元素可在 SVG 中使用，例如用於填充形狀或描邊圖形。開發者可以透過 JavaScript 來操作這些元素，進一步自定義漸變效果。

### 主要屬性
- **x1, y1**: 漸變起始點的坐標。
- **x2, y2**: 漸變結束點的坐標。
- **gradientUnits**: 定義坐標系統的單位（例如用於相對於畫布或用戶坐標系）。
- **spreadMethod**: 漸變的擴展方式（如 `pad`, `reflect`, `repeat`）。
  
### 使用方法
要使用 `SVGLinearGradientElement`，開發者需在 SVG 元素內創建一個 `<linearGradient>` 標籤，然後可以使用 JavaScript 獲取或修改這些屬性，實現動態的漸變效果。

## 示例
以下為基本用法的示例，展示如何在 SVG 中創建線性漸變：

```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

## 解釋
在使用 `SVGLinearGradientElement` 時，有幾個常見的陷阱需要注意：
- **坐標系統**: 確保了解 `x1, y1, x2, y2` 的坐標系統，以便正確定位漸變。
- **漸變的ID**: 每個漸變必須有唯一的 ID，否則可能無法正確引用。
- **性能考量**: 大量動態漸變可能影響性能，尤其是在動畫中，建議適量使用。

## 一句總結
`SVGLinearGradientElement` 讓開發者能夠在 SVG 中輕鬆創建和操作線性漸變效果。