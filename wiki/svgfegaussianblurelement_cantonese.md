<!--
Meta Description: # SVGFEGaussianBlurElement：JavaScript 中的 SVG 模糊效果元素 ## 概述 `SVGFEGaussianBlurElement` 是一個用於 SVG（可縮放向量圖形）中的濾鏡元素，用來實現高斯模糊效果。透過 JavaScript 操作此元素，開發者可以增強圖形...
Meta Keywords: svg, setattribute, svgfegaussianblurelement, javascript, const
-->

# SVGFEGaussianBlurElement：JavaScript 中的 SVG 模糊效果元素

## 概述
`SVGFEGaussianBlurElement` 是一個用於 SVG（可縮放向量圖形）中的濾鏡元素，用來實現高斯模糊效果。透過 JavaScript 操作此元素，開發者可以增強圖形的視覺效果，創造出柔和的邊緣和深度感。

## 文檔
### 目的
`SVGFEGaussianBlurElement` 的主要用途是為 SVG 圖形添加高斯模糊效果，這在設計中常用於背景模糊、陰影效果等。

### 使用方法
在 JavaScript 中，可以通過 SVG 濾鏡使用 `SVGFEGaussianBlurElement`。以下是一些主要屬性：
- `in`: 指定在哪個輸入上應用模糊效果。
- `stdDeviation`: 指定模糊的強度，這是一個數值，越大模糊效果越明顯。
- `result`: 定義輸出結果的標識符。

### 詳細信息
要使用 `SVGFEGaussianBlurElement`，首先需要創建一個 SVG 濾鏡元素，然後將其添加到目標 SVG 元素中。以下是一個基本的創建和使用過程：

1. 創建 SVG 濾鏡元素。
2. 在濾鏡中添加 `feGaussianBlur` 元素。
3. 設置屬性並將濾鏡應用到目標圖形。

範例代碼如下：

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";

// 創建 SVG 元素
const svg = document.createElementNS(svgNamespace, "svg");
const filter = document.createElementNS(svgNamespace, "filter");
const gaussianBlur = document.createElementNS(svgNamespace, "feGaussianBlur");

// 設置 Gaussian Blur 屬性
gaussianBlur.setAttribute("in", "SourceGraphic");
gaussianBlur.setAttribute("stdDeviation", "5");
filter.appendChild(gaussianBlur);
svg.appendChild(filter);

// 設置濾鏡到目標圖形
const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
rect.setAttribute("fill", "blue");
rect.setAttribute("filter", "url(#filter)");

// 將 SVG 添加到文檔
document.body.appendChild(svg);
```

## 範例
以下是幾個簡單的範例來展示如何使用 `SVGFEGaussianBlurElement`：

### 基本模糊效果
```javascript
const blurEffect = document.createElementNS(svgNamespace, "feGaussianBlur");
blurEffect.setAttribute("stdDeviation", "2");
```

### 濾鏡鏈接
```javascript
const filterUrl = "url(#myFilter)";
rect.setAttribute("filter", filterUrl);
```

## 解釋
- **常見陷阱**：確保 `stdDeviation` 的值是正數，否則將不會產生任何模糊效果。
- **性能考量**：過高的模糊數值可能會影響性能，特別是在大型圖形或動畫中使用時。
- **瀏覽器兼容性**：檢查不同瀏覽器對於 SVG 濾鏡的支持程度，以確保效果在所有環境中一致。

## 一句總結
`SVGFEGaussianBlurElement` 是一個強大的工具，能夠在 JavaScript 中為 SVG 圖形添加精美的高斯模糊效果。