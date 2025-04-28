<!--
Meta Description: # SVGLength：JavaScript 中的 SVG 長度屬性 ## 簡介 SVGLength 是一個與 SVG （可縮放向量圖形）相關的 JavaScript 物件，主要用於表示 SVG 中的長度值。它提供了對 SVG 元素長度屬性的訪問和操作，並支持不同的單位，如像素（px）、百分比（%）...
Meta Keywords: svg, svglength, width, javascript, value
-->

# SVGLength：JavaScript 中的 SVG 長度屬性

## 簡介
SVGLength 是一個與 SVG （可縮放向量圖形）相關的 JavaScript 物件，主要用於表示 SVG 中的長度值。它提供了對 SVG 元素長度屬性的訪問和操作，並支持不同的單位，如像素（px）、百分比（%）等。

## 文檔
### 目的
SVGLength 物件的主要目的是幫助開發者以編程方式讀取和修改 SVG 元素的長度屬性，這對於動態調整 SVG 圖形的大小和形狀至關重要。

### 用法
SVGLength 物件通常通過 SVG 元素的長度屬性獲取，這些屬性包括 `width`、`height`、`x` 和 `y` 等。您可以使用 JavaScript 操作這些屬性來改變圖形的顯示。

### 詳細說明
- **屬性**：
  - `value`: 返回或設置長度值，類型為數字。
  - `valueInSpecifiedUnits`: 返回長度值，使用指定的單位。
  - `unitType`: 返回當前長度的單位類型，例如 `SVG_LENGTHTYPE_PIXELS` 或 `SVG_LENGTHTYPE_PERCENTAGE`。
  - `convertToSpecifiedUnits(unitType)`: 將當前長度轉換為指定的單位。

- **單位**：
  - `SVG_LENGTHTYPE_UNKNOWN`: 未知單位。
  - `SVG_LENGTHTYPE_NUMBER`: 數字單位，通常是像素。
  - `SVG_LENGTHTYPE_PERCENTAGE`: 百分比單位。

## 範例
### 基本用法示例
```javascript
// 獲取 SVG 元素
const svgElement = document.getElementById("myRect");

// 獲取長度屬性
const width = svgElement.width.baseVal;

// 讀取當前長度值
console.log(width.value); // 輸出當前寬度值

// 修改長度值
width.value = 200; // 將寬度設置為 200 像素

// 將長度轉換為百分比
width.convertToSpecifiedUnits(SVGLength.SVG_LENGTHTYPE_PERCENTAGE);
console.log(width.value); // 輸出轉換後的百分比值
```

## 說明
在使用 SVGLength 時，開發者需要注意以下幾個常見的問題：
- **單位轉換**：在轉換單位時，如果不確定當前的單位類型，可能會導致錯誤。確保在轉換前檢查 `unitType`。
- **非數字值**：某些情況下，長度屬性可能會返回非數字值，特別是當使用百分比時。開發者需要妥善處理這些情況。
- **屬性繼承**：某些 SVG 元素的長度屬性可能會受到父元素的影響，需注意屬性繼承的情況。

## 一句總結
SVGLength 是一個用於操作 SVG 元素長度屬性的 JavaScript 物件，支持單位轉換和長度讀取。