<!--
Meta Description: # SVGFEImageElement：JavaScript 中的可擴展矢量圖像元素 ## 簡介 SVGFEImageElement 是一個在 SVG（可擴展矢量圖形）中用於嵌入位圖圖像的元素。此元素可與 JavaScript 交互，允許開發者動態控制圖像的顯示和屬性。 ## 文檔 ### 目的 S...
Meta Keywords: svg, svgfeimageelement, width, height, feimage
-->

# SVGFEImageElement：JavaScript 中的可擴展矢量圖像元素

## 簡介
SVGFEImageElement 是一個在 SVG（可擴展矢量圖形）中用於嵌入位圖圖像的元素。此元素可與 JavaScript 交互，允許開發者動態控制圖像的顯示和屬性。

## 文檔
### 目的
SVGFEImageElement 主要用於在 SVG 文件中插入外部位圖圖像。這個元素可用於創建更複雜的圖形效果，並支援多種格式的圖像，如 JPEG、PNG 和 GIF。

### 使用
在 SVG 中，SVGFEImageElement 通常作為 `<filter>` 元素的一部分出現。開發者可以通過 JavaScript 訪問和修改這些元素的屬性，例如 `href`、`width` 和 `height`。

#### 屬性
- `href`: 指定圖像的來源 URL。
- `width`: 設定圖像的寬度。
- `height`: 設定圖像的高度。
- `preserveAspectRatio`: 控制圖像的比例保持方式。

#### 方法
- `setAttribute()`: 用於動態改變元素的屬性。
- `getAttribute()`: 獲取元素的屬性值。

## 範例
以下是使用 SVGFEImageElement 的基本範例：

```html
<svg width="200" height="200">
  <defs>
    <filter id="filter1">
      <feImage href="example.png" width="100%" height="100%" />
    </filter>
  </defs>
  <rect width="200" height="200" filter="url(#filter1)" />
</svg>
```

在這個範例中，`<feImage>` 元素用於將 `example.png` 圖像應用於一個矩形的濾鏡效果。

```javascript
const feImage = document.querySelector('feImage');
feImage.setAttribute('href', 'new-image.png'); // 更改圖像來源
```

## 解釋
使用 SVGFEImageElement 時，開發者需注意以下幾點：

1. **跨域問題**：如果圖像來源是跨域的，則需要確保圖像的伺服器正確設置了 CORS 標頭，否則圖像可能無法加載。
2. **SVG 符合性**：某些舊版瀏覽器可能不支持所有 SVG 特性，必須進行適當的測試。
3. **性能考量**：過多的圖像和複雜的濾鏡效果可能會影響渲染性能，應謹慎使用。

## 總結
SVGFEImageElement 是一個功能強大的元素，允許開發者在 SVG 中動態地嵌入和控制位圖圖像，為圖形創作提供了更大的靈活性和創造性。