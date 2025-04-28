<!--
Meta Description: # SVGLength 在 JavaScript 中的應用詳解 ## 摘要 SVGLength 是一個在 SVG（可縮放向量圖形）中使用的屬性，主要用來處理長度值並在 JavaScript 中進行操作。它支持多種單位，讓開發者能夠靈活地處理 SVG 元素的大小和位置。 ## 文檔 ### 目的 SV...
Meta Keywords: svglength, svg, width, rect, value
-->

# SVGLength 在 JavaScript 中的應用詳解

## 摘要
SVGLength 是一個在 SVG（可縮放向量圖形）中使用的屬性，主要用來處理長度值並在 JavaScript 中進行操作。它支持多種單位，讓開發者能夠靈活地處理 SVG 元素的大小和位置。

## 文檔
### 目的
SVGLength 物件用於表示 SVG 元素的長度，如寬度、高度、邊距等，並提供方法來進行長度的轉換和計算。這對於動態修改 SVG 圖形非常有用。

### 使用方法
在 JavaScript 中，可以通過 SVG 元素的屬性來訪問 SVGLength 物件。例如，訪問一個 `<rect>` 元素的寬度屬性可以使用 `getAttribute()` 方法，然後將其轉換為 SVGLength 物件。

```javascript
const rect = document.querySelector('rect');
const width = rect.width.baseVal; // 獲取 SVGLength 物件
```

### 詳細描述
SVGLength 包含以下重要屬性和方法：
- `value`：返回長度值，單位依賴於當前的屬性設定。
- `unitType`：返回當前長度的單位類型，例如 `SVG_LENGTHTYPE_NUMBER` 或 `SVG_LENGTHTYPE_EMS`。
- `convertToSpecifiedUnits(unitType)`：將長度轉換為指定的單位類型。
- `newValueSpecifiedUnits(unitType, value)`：設置新的長度值及其單位。

## 範例
### 基本用法
以下是一個簡單的示例，展示如何使用 SVGLength 來修改矩形的寬度：

```html
<svg width="100" height="100">
  <rect id="myRect" width="50" height="50" fill="blue"></rect>
</svg>

<script>
  const rect = document.getElementById('myRect');
  const width = rect.width.baseVal; // 獲取寬度的 SVGLength 物件
  console.log('原始寬度:', width.value); // 輸出原始寬度

  width.value += 10; // 增加 10 單位的長度
  console.log('修改後的寬度:', width.value); // 輸出修改後的寬度
</script>
```

## 解釋
### 常見陷阱
- **單位轉換問題**：在進行長度轉換時，確保目標單位類型的正確性。如果使用不當，可能會導致圖形不顯示或錯位。
- **不支持的單位**：某些單位在 SVG 中可能不被支持，使用前需確認。
- **基於 viewport 的測量**：某些屬性（如 `viewBox`）需要基於 viewport 的尺寸來計算，這可能會影響長度的表現。

## 總結
SVGLength 是一個強大的工具，能夠幫助開發者靈活地管理和操作 SVG 元素的長度。