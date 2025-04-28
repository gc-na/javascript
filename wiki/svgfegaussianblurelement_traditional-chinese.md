<!--
Meta Description: # SVGFEGaussianBlurElement：JavaScript中的高斯模糊元素 ## 概述 SVGFEGaussianBlurElement是一個SVG（可縮放向量圖形）元素，用於在圖形中應用高斯模糊效果。透過JavaScript操作此元素，可以為SVG圖形添加視覺特效，增強用戶界面。 ...
Meta Keywords: stddeviation, filter, svg, width, 200
-->

# SVGFEGaussianBlurElement：JavaScript中的高斯模糊元素

## 概述
SVGFEGaussianBlurElement是一個SVG（可縮放向量圖形）元素，用於在圖形中應用高斯模糊效果。透過JavaScript操作此元素，可以為SVG圖形添加視覺特效，增強用戶界面。

## 文檔
### 目的
SVGFEGaussianBlurElement的主要目的是在SVG圖形上應用高斯模糊，這是一種常見的圖形處理效果，用於創造柔和的邊緣和模糊的視覺效果。

### 使用方式
在JavaScript中，SVGFEGaussianBlurElement通常與SVG的filter系統一起使用。開發者可以通過DOM操作來創建和修改此元素。

### 詳細信息
- **屬性**：
  - `in`: 指定要模糊的輸入圖像（通常是SVG圖形）。
  - `stdDeviation`: 定義模糊的程度，這是一個或兩個值，代表水平方向和垂直方向的標準偏差。
  - `result`: 定義模糊處理的輸出名稱。

- **事件**：
  - SVGFEGaussianBlurElement本身不會觸發事件，但它的屬性可以通過JavaScript事件來動態更新。

### 基本使用範例
以下是一個使用SVGFEGaussianBlurElement的簡單範例：

```html
<svg width="200" height="200">
  <defs>
    <filter id="blurFilter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="orange" filter="url(#blurFilter)" />
</svg>
```

#### 使用JavaScript來動態修改
```javascript
const blurElement = document.querySelector('feGaussianBlur');
blurElement.setAttribute('stdDeviation', '10');
```

## 解釋
### 常見問題
- **不顯示模糊效果**：確認`filter`的`in`屬性正確指向要模糊的圖形。如果`in`設為錯誤的值，將無法獲得期望的模糊效果。
- **性能問題**：高斯模糊可能會影響性能，特別是在大型圖形上。建議在不需要時關閉模糊效果，或考慮使用較低的模糊程度。

### 附加注意事項
- 確保瀏覽器支持SVG和高斯模糊效果，某些舊版瀏覽器可能無法正常顯示。
- 使用`stdDeviation`時，提供一個值將在水平方向和垂直方向上應用相同的模糊；如果提供兩個值，第一個為水平模糊度，第二個為垂直模糊度。

## 一句話總結
SVGFEGaussianBlurElement是用於在SVG中應用高斯模糊效果的元素，能夠通過JavaScript輕鬆地動態調整模糊參數。