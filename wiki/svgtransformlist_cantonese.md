<!--
Meta Description: # SVGTransformList 在 JavaScript 中的應用 ## 概述 SVGTransformList 是一個用於操作 SVG（可縮放矢量圖形）轉換的 JavaScript 物件。它提供了一個集合，可以包含多個轉換（如平移、縮放、旋轉等），用於改變 SVG 元素的顯示方式。 ## 文...
Meta Keywords: svg, svgtransformlist, javascript, rect, transforms
-->

# SVGTransformList 在 JavaScript 中的應用

## 概述
SVGTransformList 是一個用於操作 SVG（可縮放矢量圖形）轉換的 JavaScript 物件。它提供了一個集合，可以包含多個轉換（如平移、縮放、旋轉等），用於改變 SVG 元素的顯示方式。

## 文檔
SVGTransformList 主要用於管理與 SVG 元素相關的轉換。這包括創建、刪除和修改轉換。每個 SVG 元素都可以有一個與之相關聯的 SVGTransformList，該列表中的每個轉換都會影響元素的顯示。

### 主要功能：
- **添加轉換**：可以將新的轉換添加到列表中。
- **刪除轉換**：可以從列表中刪除現有的轉換。
- **訪問轉換**：可通過索引訪問列表中的轉換。
- **修改轉換**：可以改變已存在的轉換屬性。

### 使用方法：
要訪問 SVGTransformList，可以使用 `SVGElement` 的 `transform.baseVal` 屬性，該屬性返回一個 SVGTransformList 實例。

## 示例
以下是一些基本的使用範例：

### 創建 SVG 矩形並添加轉換
```javascript
// 獲取 SVG 元素
const svg = document.getElementById('mySvg');
const rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("width", 100);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "blue");
svg.appendChild(rect);

// 獲取轉換列表並添加轉換
const transforms = rect.transform.baseVal;
const translate = svg.createSVGTransform();
translate.setTranslate(50, 50);
transforms.appendItem(translate);
```

### 刪除轉換
```javascript
// 刪除第一個轉換
if (transforms.numberOfItems > 0) {
    transforms.removeItem(0);
}
```

### 修改轉換
```javascript
// 修改第二個轉換（如果存在）
if (transforms.numberOfItems > 1) {
    const scale = transforms.getItem(1);
    scale.setScale(2, 2);
}
```

## 解釋
使用 SVGTransformList 時，有幾個常見問題需要注意：
- **轉換順序**：轉換是按照添加的順序進行計算的，這意味著先添加的轉換會影響後添加的轉換。
- **轉換類型**：確保使用正確的轉換類型（如平移、旋轉、縮放），否則可能會導致意想不到的效果。
- **不支持的瀏覽器**：某些舊版瀏覽器可能不完全支持 SVG 和相關的 JavaScript API，因此在開發時要進行相容性測試。

## 一句話總結
SVGTransformList 在 JavaScript 中用於管理和操作 SVG 元素的轉換，提供靈活的顯示控制能力。