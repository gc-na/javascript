<!--
Meta Description: # SVGFEConvolveMatrixElement：JavaScript 中的 SVG 濾鏡矩陣元素 ## 簡介 `SVGFEConvolveMatrixElement` 是一個在 SVG（可縮放矢量圖形）中用來應用卷積矩陣濾鏡的元素。它允許開發者對圖形進行圖像處理，實現模糊、銳化等效果，並在...
Meta Keywords: svg, svgfeconvolvematrixelement, filter, kernelmatrix, javascript
-->

# SVGFEConvolveMatrixElement：JavaScript 中的 SVG 濾鏡矩陣元素

## 簡介
`SVGFEConvolveMatrixElement` 是一個在 SVG（可縮放矢量圖形）中用來應用卷積矩陣濾鏡的元素。它允許開發者對圖形進行圖像處理，實現模糊、銳化等效果，並在 JavaScript 中提供了操作這些濾鏡的接口。

## 文檔
### 目的
`SVGFEConvolveMatrixElement` 用於定義一個卷積濾鏡，能夠對 SVG 圖形進行複雜的圖像處理。這個濾鏡通過應用一個指定的矩陣來改變圖像的像素值，從而實現各種視覺效果。

### 用法
在 JavaScript 中，`SVGFEConvolveMatrixElement` 可以通過 `createElementNS` 方法創建。以下是一些重要屬性和方法的簡要說明：

- `kernelMatrix`：定義應用於圖像的卷積矩陣。
- `divisor`：分母，用於標準化卷積計算。
- `bias`：加到每個像素值上的偏差。
- `targetX` 和 `targetY`：定義矩陣的中心點。
- `edgeMode`：定義邊緣處理的模式。

示例：
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const filter = document.createElementNS(svgNS, "filter");
const convolveMatrix = document.createElementNS(svgNS, "feConvolveMatrix");

convolveMatrix.setAttribute("kernelMatrix", "1 1 1 1 1 1 1 1 1");
convolveMatrix.setAttribute("divisor", "9");
filter.appendChild(convolveMatrix);
```

### 詳細說明
在使用 `SVGFEConvolveMatrixElement` 時，開發者需注意以下幾點：

1. **矩陣尺寸**：`kernelMatrix` 的維度必須為奇數，通常為 3x3 或 5x5。
2. **邊緣模式**：`edgeMode` 屬性可以設定為 `duplicate`、`wrap` 或 `none`，影響濾鏡在邊緣處的行為。
3. **性能考量**：過於複雜的卷積矩陣可能會影響性能，特別是在大型圖像上。

## 範例
以下是一個應用 `SVGFEConvolveMatrixElement` 的基本範例，展示如何在 SVG 中創建一個簡單的銳化濾鏡：

```html
<svg width="200" height="200">
    <defs>
        <filter id="sharpness">
            <feConvolveMatrix kernelMatrix="0  -1  0
                                             -1  5 -1
                                             0  -1  0" 
                              divisor="1" />
        </filter>
    </defs>
    <image xlink:href="image.png" filter="url(#sharpness)" />
</svg>
```

## 解釋
在使用 `SVGFEConvolveMatrixElement` 時，開發者需注意常見的陷阱：

- **矩陣解析錯誤**：確保 `kernelMatrix` 的格式正確，否則可能會導致濾鏡無法正確應用。
- **性能問題**：在處理大型圖像或多個濾鏡時，應考慮性能影響，避免造成頁面卡頓。
- **瀏覽器兼容性**：某些舊版瀏覽器可能不完全支持 SVG 濾鏡功能，建議進行測試。

## 總結
`SVGFEConvolveMatrixElement` 是一個強大的工具，允許開發者使用卷積矩陣對 SVG 圖形進行高效的圖像處理。