<!--
Meta Description: # SVGFEBlendElement：JavaScript 中的 SVG 濾鏡元素 ## 概要 SVGFEBlendElement 是一個 SVG 濾鏡元素，用於將兩個圖像或圖形混合在一起，透過不同的混合模式來創造視覺效果。在 JavaScript 中，這個元素可以動態地添加到 SVG 中，並且可...
Meta Keywords: svg, svgfeblendelement, filter, 200, width
-->

# SVGFEBlendElement：JavaScript 中的 SVG 濾鏡元素

## 概要
SVGFEBlendElement 是一個 SVG 濾鏡元素，用於將兩個圖像或圖形混合在一起，透過不同的混合模式來創造視覺效果。在 JavaScript 中，這個元素可以動態地添加到 SVG 中，並且可以通過腳本控制其屬性。

## 文檔
SVGFEBlendElement 的主要用途是混合兩個來源的圖像，這些來源可以是圖形元素或其他 SVG 元素。這個元素支持多種混合模式，例如「正常」、「疊加」和「乘法」，用戶可以根據需要選擇。

### 用法
要使用 SVGFEBlendElement，首先需要在 SVG 中定義一個 `<filter>` 元素，然後添加 `<feBlend>` 作為其子元素。以下是基本的結構：

```html
<svg>
  <defs>
    <filter id="blendFilter">
      <feBlend in="SourceGraphic" in2="BackgroundImage" mode="multiply" />
    </filter>
  </defs>
  <rect width="100" height="100" fill="red" filter="url(#blendFilter)" />
  <image href="background.png" width="100" height="100" />
</svg>
```

在 JavaScript 中，可以通過創建 SVGFEBlendElement 的實例並設置其屬性來動態添加或修改此元素。

### 主要屬性
- `in`: 定義第一個輸入源。
- `in2`: 定義第二個輸入源。
- `mode`: 設定混合模式，可選值包括 `normal`, `multiply`, `screen`, `overlay`, `darken`, `lighten` 等。

## 示例
以下是 SVGFEBlendElement 的基本使用示例：

```html
<svg width="200" height="200">
  <defs>
    <filter id="blendFilter">
      <feBlend in="SourceGraphic" in2="BackgroundImage" mode="screen" />
    </filter>
  </defs>
  <rect width="200" height="200" fill="blue" filter="url(#blendFilter)" />
  <image href="image.png" width="200" height="200" />
</svg>
```

在這個例子中，藍色矩形和背景圖像使用「screen」模式混合，產生亮度增強的效果。

## 解釋
使用 SVGFEBlendElement 時，有幾個常見的注意事項：
- 確保所引用的圖像或圖形存在，否則混合將不會顯示效果。
- 混合模式的選擇會顯著影響最終的視覺結果，因此選擇合適的模式至關重要。
- 當動態更改屬性時，可能需要手動刷新渲染以顯示更新。

## 一行總結
SVGFEBlendElement 是一個強大的 SVG 元素，能夠在 JavaScript 中實現靈活的圖像混合效果。