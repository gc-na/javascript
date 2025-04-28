<!--
Meta Description: # SVGAnimatedLength：JavaScript 中的動畫長度屬性 ## 概述 SVGAnimatedLength 是 SVG（可擴展向量圖形）中用來表示可動畫的長度屬性，並可通過 JavaScript 進行操作。它允許開發者在 SVG 元素中使用動畫效果，使其長度在不同的狀態之間過渡。...
Meta Keywords: line, svganimatedlength, svg, javascript, style
-->

# SVGAnimatedLength：JavaScript 中的動畫長度屬性

## 概述
SVGAnimatedLength 是 SVG（可擴展向量圖形）中用來表示可動畫的長度屬性，並可通過 JavaScript 進行操作。它允許開發者在 SVG 元素中使用動畫效果，使其長度在不同的狀態之間過渡。

## 文檔
### 目的
SVGAnimatedLength 的主要目的是提供一種方式來定義和操作 SVG 元素的長度屬性，這些屬性可以是靜態的或動畫的。

### 使用方法
SVGAnimatedLength 主要用於 SVG 元素的長度屬性，例如 `<line>`、`<rect>`、`<circle>` 等。它包含兩個屬性：`baseVal` 和 `animVal`。

- `baseVal`：表示該長度的基本值。
- `animVal`：表示動畫結束時的長度值。

這些屬性可以通過 JavaScript 進行訪問和修改，從而實現動態效果。

### 詳細信息
- **屬性類型**：SVGAnimatedLength 是一個對象，提供了兩個 SVGLength 類型的屬性。
- **使用場景**：適用於需要在視覺上表現變化的場景，如動畫圖形、過渡效果等。

## 示例
以下是使用 SVGAnimatedLength 的基本範例：

```html
<svg width="200" height="200">
  <line id="myLine" x1="0" y1="0" x2="100" y2="100" stroke="black" />
</svg>

<script>
  const line = document.getElementById('myLine');
  const length = line.getTotalLength(); // 獲取總長度
  line.style.strokeDasharray = length; // 設置虛線效果
  line.style.strokeDashoffset = length; // 初始化偏移量

  // 動畫過渡
  line.getBoundingClientRect(); // 觸發重排
  line.style.transition = 'stroke-dashoffset 2s ease-in-out';
  line.style.strokeDashoffset = '0'; // 將偏移量設置為 0
</script>
```

## 解釋
### 常見陷阱
1. **動畫效果不顯示**：確保在設置動畫屬性之前，觸發 DOM 重排（例如通過訪問 `getBoundingClientRect`）。
2. **屬性訪問錯誤**：確保使用正確的屬性名稱來訪問 `baseVal` 和 `animVal`。

### 注意事項
- SVGAnimatedLength 的動畫效果可能會受到 CSS 的影響，因此在設置樣式時需謹慎。
- 在使用 JavaScript 操作動畫屬性時，確保對性能進行考量，避免不必要的重排和重繪。

## 總結
SVGAnimatedLength 使得在 JavaScript 中操作 SVG 元素的長度屬性變得簡單，並且支持動畫效果的實現。