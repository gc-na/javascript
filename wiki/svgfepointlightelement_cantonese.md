<!--
Meta Description: # SVGFEPointLightElement：JavaScript 中的點光源元素 ## 簡介 SVGFEPointLightElement 是一個用於 SVG（可縮放矢量圖形）的 JavaScript 物件，代表一個點光源，該光源可以用來為場景中的物件提供照明效果。它在 2D 圖形和動畫中廣泛...
Meta Keywords: svg, filter, svgfepointlightelement, 200, defs
-->

# SVGFEPointLightElement：JavaScript 中的點光源元素

## 簡介
SVGFEPointLightElement 是一個用於 SVG（可縮放矢量圖形）的 JavaScript 物件，代表一個點光源，該光源可以用來為場景中的物件提供照明效果。它在 2D 圖形和動畫中廣泛應用，以增強視覺效果。

## 文檔
### 目的
SVGFEPointLightElement 用於創建光源的效果，主要用於 SVG 的 <filter> 元素中。這個元素可以影響到其他 SVG 元素的顯示方式，使其看起來更立體和動態。

### 使用方法
要使用 SVGFEPointLightElement，首先需要建立一個 SVG 元素，然後在這個元素內部定義 <filter>，最後加入 <fePointLight> 來設置光源。以下是基本的結構：

```html
<svg width="200" height="200">
  <defs>
    <filter id="myFilter">
      <fePointLight x="50" y="50" z="10" />
    </filter>
  </defs>
  <circle cx="100" cy="100" r="50" fill="red" filter="url(#myFilter)" />
</svg>
```

### 詳細信息
- **屬性**：
  - `x`: 定義光源的 X 坐標。
  - `y`: 定義光源的 Y 坐標。
  - `z`: 定義光源的 Z 坐標，影響光的強度。

- **支援度**：SVGFEPointLightElement 在現代瀏覽器中被廣泛支持，但在一些舊瀏覽器中可能存在兼容性問題。

## 示例
以下是使用 SVGFEPointLightElement 的幾個基本示例：

### 示例 1：簡單的點光源
```html
<svg width="200" height="200">
  <defs>
    <filter id="lighting">
      <fePointLight x="100" y="100" z="50" />
    </filter>
  </defs>
  <rect x="50" y="50" width="100" height="100" fill="blue" filter="url(#lighting)" />
</svg>
```

### 示例 2：移動的光源
```html
<svg width="400" height="400">
  <defs>
    <filter id="dynamicLight">
      <fePointLight x="200" y="200" z="30" />
    </filter>
  </defs>
  <circle cx="200" cy="200" r="80" fill="green" filter="url(#dynamicLight)" />
</svg>
```

## 解釋
使用 SVGFEPointLightElement 時，開發者需要注意以下幾點：
- 確保光源的 Z 坐標值適當，因為它會影響到照明的強度。如果 Z 值設置得太小，可能會導致光源效果不明顯。
- 確認 SVG 和 CSS 的兼容性，因為某些樣式可能會影響到光源效果的顯示。
- 測試不同的瀏覽器，以確保功能正常，特別是在舊版瀏覽器中。

## 一句總結
SVGFEPointLightElement 是一個強大的工具，可以在 JavaScript 中創建動態且立體的光源效果，以增強 SVG 圖形的視覺效果。