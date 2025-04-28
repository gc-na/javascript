<!--
Meta Description: # SVGTransform：JavaScript 中的可縮放向量圖形變換 ## 簡介 SVGTransform 是一個在 JavaScript 中操作可縮放向量圖形（SVG）元素的工具，主要用於對圖形進行變換，如平移、旋轉、縮放和傾斜。這個功能使得開發者能夠在網頁上靈活地操控圖形的外觀和位置。 #...
Meta Keywords: transform, svgelement, let, baseval, svgtransform
-->

# SVGTransform：JavaScript 中的可縮放向量圖形變換

## 簡介
SVGTransform 是一個在 JavaScript 中操作可縮放向量圖形（SVG）元素的工具，主要用於對圖形進行變換，如平移、旋轉、縮放和傾斜。這個功能使得開發者能夠在網頁上靈活地操控圖形的外觀和位置。

## 文檔
### 目的
SVGTransform 的主要目的是提供一種方法，讓開發者能夠對 SVG 元素進行各種變換操作，這些變換可以直接影響圖形的顯示效果。

### 使用方法
SVGTransform 是在 SVG DOM 中使用的對象，通常與 `SVGMatrix` 和 `SVGElement` 相關聯。可以通過 `transform` 屬性來訪問和修改。

#### 基本語法
```javascript
let svgElement = document.getElementById("mySvgElement");
let transform = svgElement.transform.baseVal.createSVGTransform();
```

### 詳細說明
`SVGTransform` 提供了以下幾種主要的變換類型：

- **平移 (Translate)**: 使用 `setTranslate(tx, ty)` 方法，將圖形沿 X 和 Y 軸移動。
- **旋轉 (Rotate)**: 使用 `setRotate(angle, cx, cy)` 方法，圍繞指定的中心點進行旋轉。
- **縮放 (Scale)**: 使用 `setScale(sx, sy)` 方法，改變圖形的大小。
- **傾斜 (Skew)**: 使用 `setSkewX(angle)` 和 `setSkewY(angle)` 方法，對圖形進行傾斜變換。

這些變換可以單獨使用，也可以組合使用來創建複雜的效果。

## 範例
### 基本平移範例
```javascript
let svgElement = document.getElementById("mySvgElement");
let transform = svgElement.transform.baseVal.createSVGTransform();
transform.setTranslate(50, 50);
svgElement.transform.baseVal.appendItem(transform);
```

### 旋轉範例
```javascript
let svgElement = document.getElementById("mySvgElement");
let transform = svgElement.transform.baseVal.createSVGTransform();
transform.setRotate(45, 100, 100);
svgElement.transform.baseVal.appendItem(transform);
```

### 縮放範例
```javascript
let svgElement = document.getElementById("mySvgElement");
let transform = svgElement.transform.baseVal.createSVGTransform();
transform.setScale(2, 2);
svgElement.transform.baseVal.appendItem(transform);
```

## 說明
在使用 SVGTransform 時，開發者可能會遇到以下常見問題：

- **變換順序**: SVG 中的變換是累加的，變換的順序會影響最終效果。例如，先縮放再平移與先平移再縮放的效果是不同的。
- **不可直接修改**: `baseVal` 屬性返回的是一個只讀的集合，對其進行操作時需要使用 `appendItem()` 或 `removeItem()` 方法。
- **性能考量**: 大量的變換操作可能會影響性能，特別是在動畫或動態更新的情況下，建議合理使用。

## 一句總結
SVGTransform 是 JavaScript 中操作 SVG 元素的強大工具，能夠實現圖形的平移、旋轉、縮放和傾斜等變換。