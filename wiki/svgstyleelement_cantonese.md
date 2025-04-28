<!--
Meta Description: # SVGStyleElement：JavaScript 中的 SVG 樣式元素 ## 簡介 `SVGStyleElement` 係一個用於定義 SVG (可縮放矢量圖形) 中樣式的元素，通常用來包含 CSS 規則。佢可以幫助開發者為 SVG 圖形應用樣式，提升圖形的外觀和可讀性。 ## 文檔 `S...
Meta Keywords: svg, svgstyleelement, css, style, circle
-->

# SVGStyleElement：JavaScript 中的 SVG 樣式元素

## 簡介
`SVGStyleElement` 係一個用於定義 SVG (可縮放矢量圖形) 中樣式的元素，通常用來包含 CSS 規則。佢可以幫助開發者為 SVG 圖形應用樣式，提升圖形的外觀和可讀性。

## 文檔
`SVGStyleElement` 係一個擴展自 `SVGElement` 的接口，提供了一種方式來包含 CSS 樣式於 SVG 文檔中。佢的作用主要包括：

- **目的**：允許開發者直接在 SVG 中嵌入 CSS 樣式，從而控制 SVG 元素的外觀。
- **使用**：可以通過 JavaScript 創建一個 `SVGStyleElement` 實例，然後將其添加到 SVG 文檔中。
- **屬性**：
  - `type`: 定義樣式的類型，通常為 `text/css`。
  - `media`: 用來指定樣式適用的媒介，例如 `screen` 或 `print`。
  - `title`: 提供樣式的標題。

### 語法
```javascript
let styleElement = document.createElementNS("http://www.w3.org/2000/svg", "style");
```

## 示例
以下係一個基本使用 `SVGStyleElement` 嘅例子：

```javascript
// 創建 SVG 和 style 元素
let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let style = document.createElementNS("http://www.w3.org/2000/svg", "style");

// 設定樣式
style.textContent = `
  .red {
    fill: red;
  }
  .blue {
    fill: blue;
  }
`;

// 將 style 元素加入到 SVG 中
svg.appendChild(style);

// 創建一個圓形並應用樣式
let circle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
circle.setAttribute("class", "red");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");

// 將圓形加入到 SVG 中
svg.appendChild(circle);

// 將 SVG 加入到文檔中
document.body.appendChild(svg);
```

## 解釋
使用 `SVGStyleElement` 時，有幾個常見的注意事項：

- **樣式優先級**：如果在外部 CSS 和 `SVGStyleElement` 中同時定義了樣式，則外部 CSS 的優先級會更高。
- **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持 SVG 和 CSS，但某些舊版瀏覽器可能不完全支持 CSS 在 SVG 中的使用。
- **性能考量**：在大型 SVG 文件中，過多的內聯樣式可能會影響性能，因此應謹慎使用。

## 總結
`SVGStyleElement` 係一個強大嘅工具，可以幫助開發者在 SVG 圖形中輕鬆應用樣式，提升視覺效果和可讀性。