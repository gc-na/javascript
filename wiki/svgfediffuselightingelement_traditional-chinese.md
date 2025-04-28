<!--
Meta Description: # SVGFEDiffuseLightingElement：JavaScript 中的 SVG 擴散照明元素 ## 概述 `SVGFEDiffuseLightingElement` 是一個用於 SVG（可縮放向量圖形）的元素，專門用於創建擴散光照效果。它可以與其他 SVG 元素結合使用，以增強圖形的...
Meta Keywords: svg, filter, svgfediffuselightingelement, fediffuselighting, surfacescale
-->

# SVGFEDiffuseLightingElement：JavaScript 中的 SVG 擴散照明元素

## 概述
`SVGFEDiffuseLightingElement` 是一個用於 SVG（可縮放向量圖形）的元素，專門用於創建擴散光照效果。它可以與其他 SVG 元素結合使用，以增強圖形的三維感和深度感。

## 文檔
`SVGFEDiffuseLightingElement` 是 SVG 濾鏡的一部分，主要用於模擬光的擴散效果。此元素通常與 `filter` 元素結合使用，並需要指定光源和光的強度，以便在圖形上創建生動的照明效果。

### 主要屬性
- `in`: 表示要應用濾鏡的輸入圖像。
- `surfaceScale`: 控制表面光滑度的比例。
- `diffuseConstant`: 控制擴散光強度的常數值。
- `kernelUnitLength`: 定義濾鏡內部的單位長度。

### 使用方法
要使用 `SVGFEDiffuseLightingElement`，您需要在 SVG 文件中定義一個濾鏡，然後在需要的元素上引用該濾鏡。這通常包括：
1. 定義一個 `filter` 元素。
2. 在該濾鏡內添加 `feDiffuseLighting` 元素。
3. 設置所需的屬性以調整照明效果。

```html
<svg width="200" height="200">
    <defs>
        <filter id="diffuseLighting">
            <feDiffuseLighting in="SourceGraphic" surfaceScale="5" diffuseConstant="1">
                <light x="50%" y="50%" z="1000"/>
            </feDiffuseLighting>
        </filter>
    </defs>
    <rect width="100%" height="100%" fill="orange" filter="url(#diffuseLighting)"/>
</svg>
```

## 範例
以下是使用 `SVGFEDiffuseLightingElement` 的基本範例：

```html
<svg width="300" height="300">
    <defs>
        <filter id="lightEffect">
            <feDiffuseLighting in="SourceGraphic" surfaceScale="1" diffuseConstant="2">
                <light x="50%" y="50%" z="200"/>
            </feDiffuseLighting>
        </filter>
    </defs>
    <circle cx="150" cy="150" r="100" fill="blue" filter="url(#lightEffect)"/>
</svg>
```

這段程式碼將在藍色圓形上添加擴散光照效果，使其看起來更具立體感。

## 解釋
使用 `SVGFEDiffuseLightingElement` 時，需注意以下幾點：
- 確保在 `filter` 元素內正確配置 `light` 元素，否則照明效果可能不如預期。
- `surfaceScale` 和 `diffuseConstant` 的值會直接影響最終效果，建議進行多次嘗試以獲得理想的光照效果。
- 此類濾鏡在某些舊版瀏覽器中可能不支持，因此在開發過程中應注意兼容性問題。

## 一句總結
`SVGFEDiffuseLightingElement` 是一個強大的 SVG 濾鏡元素，能夠為圖形添加生動的擴散光照效果。