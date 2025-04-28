<!--
Meta Description: # SVGImageElement：JavaScript 中的 SVG 圖像元素 ## 概述 `SVGImageElement` 是一種在 SVG (可縮放矢量圖形) 中用於表示圖像的元素，通常用於在網頁中嵌入位圖圖像，並可使用 JavaScript 進行操作和控制。 ## 文檔 `SVGImage...
Meta Keywords: svg, svgimageelement, javascript, img, width
-->

# SVGImageElement：JavaScript 中的 SVG 圖像元素

## 概述
`SVGImageElement` 是一種在 SVG (可縮放矢量圖形) 中用於表示圖像的元素，通常用於在網頁中嵌入位圖圖像，並可使用 JavaScript 進行操作和控制。

## 文檔
`SVGImageElement` 是 SVG 中的一個元素，對應於 HTML 中的 `<img>` 標籤。它的主要目的是顯示外部圖像，並且可以通過 JavaScript 進行屬性設置和事件監聽。此元素的主要屬性包括：

- `href`：指定要顯示的圖像的 URL。
- `width`：設置圖像的寬度。
- `height`：設置圖像的高度。
- `preserveAspectRatio`：定義如何縮放圖像以適應其容器。

在使用 `SVGImageElement` 時，您可以直接在 SVG 中定義圖像，或使用 JavaScript 動態創建和操作此元素。

### 使用方法
以下是創建和使用 `SVGImageElement` 的基本步驟：

1. 創建 SVG 元素。
2. 創建 `SVGImageElement` 的實例，並設置相關屬性。
3. 將圖像元素添加到 SVG 中。

## 示例
以下是一些基本用法的範例：

### 基本示例
```html
<svg width="200" height="200">
  <image href="https://example.com/image.png" width="100" height="100" />
</svg>
```

### 使用 JavaScript 動態創建
```html
<svg id="mySVG" width="200" height="200"></svg>

<script>
  const svg = document.getElementById('mySVG');
  const img = document.createElementNS('http://www.w3.org/2000/svg', 'image');
  
  img.setAttribute('href', 'https://example.com/image.png');
  img.setAttribute('width', '100');
  img.setAttribute('height', '100');
  
  svg.appendChild(img);
</script>
```

## 解釋
在使用 `SVGImageElement` 時，開發者常常會遇到以下幾個常見問題：

- **跨域問題**：如果圖像來源於不同的網域，可能會出現 CORS（跨來源資源共享）問題，導致圖像無法顯示。
- **屬性設置**：確保正確使用 SVG 命名空間，否則可能無法創建或操作圖像元素。
- **顯示問題**：如果未正確設置寬度和高度，圖像可能無法正確顯示或變形。

## 總結
`SVGImageElement` 是一個強大的工具，用於在 SVG 中嵌入和操作圖像，提供了靈活的屬性選擇，並能夠與 JavaScript 進行互動。