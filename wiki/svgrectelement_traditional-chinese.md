<!--
Meta Description: # SVGRectElement：JavaScript中的矩形元素 ## 摘要 SVGRectElement是SVG（可縮放向量圖形）中的一個接口，代表矩形形狀。它在JavaScript中可以被操作，以便創建和修改SVG圖形中的矩形元素。 ## 文件說明 SVGRectElement是一種特定的SV...
Meta Keywords: width, rect, height, getbbox, setattribute
-->

# SVGRectElement：JavaScript中的矩形元素

## 摘要
SVGRectElement是SVG（可縮放向量圖形）中的一個接口，代表矩形形狀。它在JavaScript中可以被操作，以便創建和修改SVG圖形中的矩形元素。

## 文件說明
SVGRectElement是一種特定的SVG圖形元素，用於定義和操作矩形。這個接口提供了多種屬性和方法來設置矩形的大小、位置和樣式。它繼承自SVGShapeElement，因此可以使用SVG的所有通用屬性和方法。

### 主要屬性
- `x`：矩形的左上角的X坐標。
- `y`：矩形的左上角的Y坐標。
- `width`：矩形的寬度。
- `height`：矩形的高度。
- `rx`：矩形的圓角半徑（X軸）。
- `ry`：矩形的圓角半徑（Y軸）。

### 主要方法
- `getBBox()`：返回矩形的邊界框。
- `setAttribute(name, value)`：設置指定屬性的值。

## 例子
### 創建一個簡單的SVG矩形
```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="50" fill="blue"/>
</svg>
```

### 使用JavaScript修改矩形屬性
```javascript
const rect = document.getElementById("myRect");
rect.setAttribute("fill", "red"); // 將矩形顏色改為紅色
rect.setAttribute("width", 150); // 將矩形寬度改為150
```

### 獲取矩形的邊界框
```javascript
const bbox = rect.getBBox();
console.log(bbox); // 輸出矩形的邊界框資訊
```

## 解釋
在使用SVGRectElement時，有幾個常見的陷阱需要注意：
- 確保在操作矩形之前，SVG元素已經被加載到DOM中。
- 設置屬性時，屬性值應該是有效的數字（例如，`width`和`height`不能為負值）。
- 使用`getBBox()`方法獲取的邊界框是相對於SVG的坐標系統。

## 單行摘要
SVGRectElement是JavaScript中用於創建和操作SVG矩形元素的接口。