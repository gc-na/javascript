<!--
Meta Description: # SVGLengthList：JavaScript 中的 SVG 長度列表 ## 簡介 SVGLengthList 是一個用於處理 SVG（可縮放矢量圖形）中長度值的 JavaScript 物件。這個物件允許開發者管理和操作 SVG 元素的長度屬性，提供了一個靈活的方式來動態修改圖形的尺寸。 ##...
Meta Keywords: svg, svglengthlist, dasharray, svglength, let
-->

# SVGLengthList：JavaScript 中的 SVG 長度列表

## 簡介
SVGLengthList 是一個用於處理 SVG（可縮放矢量圖形）中長度值的 JavaScript 物件。這個物件允許開發者管理和操作 SVG 元素的長度屬性，提供了一個靈活的方式來動態修改圖形的尺寸。

## 文檔
SVGLengthList 的主要目的是為了方便操作 SVG 中的長度屬性，特別是那些需要多個長度值的屬性，如 `stroke-dasharray` 或 `path` 的某些屬性。這個物件提供了一個集合，能夠存儲多個 SVGLength 物件，並提供了一系列方法來訪問和操作這些長度值。

### 使用方法
SVGLengthList 通常由瀏覽器自動創建，當你訪問 SVG 元素的某個長度屬性時，它會返回一個 SVGLengthList 物件。例如：

```javascript
let rect = document.querySelector('rect');
let lengthList = rect.getAttribute('stroke-dasharray');
```

### 詳細信息
- **屬性**:
  - `numberOfItems`: 返回 SVGLengthList 中項目的數量。
  
- **方法**:
  - `appendItem()`: 在列表末尾添加一個新的 SVGLength。
  - `clear()`: 清除列表中的所有項目。
  - `getItem(index)`: 根據索引獲取特定的 SVGLength。
  - `initialize()`: 用新的 SVGLength 物件初始化列表。
  - `removeItem(index)`: 根據索引移除特定的 SVGLength。
  - `replaceItem(newItem, index)`: 用新的 SVGLength 替換指定索引的項目。

## 示例
以下是一些基本的使用範例：

```javascript
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let rectElement = document.createElementNS("http://www.w3.org/2000/svg", "rect");

rectElement.setAttribute("stroke-dasharray", "5, 5");
let dashArray = rectElement.getAttribute("stroke-dasharray");
console.log(dashArray); // 輸出: "5, 5"

let lengthList = rectElement.strokeDasharray; // 獲取 SVGLengthList
console.log(lengthList.numberOfItems); // 輸出: 2

lengthList.appendItem(svgElement.createSVGLength(10)); // 添加一個新的長度
console.log(lengthList.numberOfItems); // 輸出: 3
```

## 解釋
在使用 SVGLengthList 時，有一些常見的陷阱和注意事項：
- 確保正確使用命名空間，因為 SVG 元素必須使用 `createElementNS` 來創建。
- 當添加或刪除項目時，請注意索引從 0 開始。
- 對於某些屬性，如 `stroke-dasharray`，必須確保長度值的格式正確。

## 一句話總結
SVGLengthList 是一個用於操作 SVG 長度屬性的 JavaScript 物件，提供了靈活的管理和修改方式。