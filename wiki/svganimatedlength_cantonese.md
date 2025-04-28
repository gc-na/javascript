<!--
Meta Description: # SVGAnimatedLength：JavaScript 中的可動畫長度屬性 ## 概述 SVGAnimatedLength 是一個與 SVG（可縮放矢量圖形）相關的屬性，允許在 JavaScript 中處理與長度相關的動畫。它提供了一種方便的方法來管理 SVG 元素的長度屬性，並支援動畫效果。...
Meta Keywords: svg, svganimatedlength, javascript, baseval, 元素的長度屬性
-->

# SVGAnimatedLength：JavaScript 中的可動畫長度屬性

## 概述
SVGAnimatedLength 是一個與 SVG（可縮放矢量圖形）相關的屬性，允許在 JavaScript 中處理與長度相關的動畫。它提供了一種方便的方法來管理 SVG 元素的長度屬性，並支援動畫效果。

## 文件
SVGAnimatedLength 主要用於表示 SVG 元素的長度屬性，這些屬性可以是固定的或是可動畫的。這些長度屬性通常用於定義 SVG 的寬度、高度、半徑等。

### 目的
SVGAnimatedLength 使開發者能夠輕鬆地在 JavaScript 中控制 SVG 元素的長度屬性，並創建動態的視覺效果。

### 使用方法
SVGAnimatedLength 屬性通常用於以下 SVG 元素中：
- `line`
- `rect`
- `circle`
- `ellipse`
- `path`
- `polyline`
- `polygon`

每個 SVG 元素的長度屬性（如 `width`、`height`、`rx`、`ry` 等）都可以被定義為 SVGAnimatedLength。

### 詳情
SVGAnimatedLength 由兩個主要部分組成：
- `baseVal`：表示該屬性的基本值。
- `animVal`：表示動畫過程中的值。

這兩個屬性可以透過 JavaScript 進行訪問和修改，從而實現動畫效果。

```javascript
const rect = document.querySelector('rect');
const length = rect.width;

// 獲取基本值
console.log(length.baseVal.value);

// 設定新的基本值
length.baseVal.value = 100;
```

## 示例
以下是一個簡單的例子，演示如何使用 SVGAnimatedLength 來改變 SVG 圓的半徑：

```html
<svg width="200" height="200">
  <circle id="myCircle" cx="100" cy="100" r="50" fill="blue" />
</svg>

<script>
  const circle = document.getElementById('myCircle');
  const radius = circle.r;

  // 獲取和修改圓的半徑
  console.log(radius.baseVal.value); // 輸出：50
  radius.baseVal.value = 75; // 更改半徑
</script>
```

## 解釋
使用 SVGAnimatedLength 時，開發者應注意以下幾點：
- 確認所選擇的 SVG 元素支持該屬性。
- 在修改 `baseVal` 時，將會影響實際的 SVG 元素外觀，但 `animVal` 不會立即更新。
- 動畫效果需要正確設置和觸發，否則可能會導致意想不到的行為。

## 一句總結
SVGAnimatedLength 是一個強大的工具，使開發者能夠在 JavaScript 中輕鬆管理 SVG 元素的長度屬性並實現動畫效果。