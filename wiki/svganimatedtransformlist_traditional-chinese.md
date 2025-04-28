<!--
Meta Description: # SVGAnimatedTransformList：JavaScript 中的可動畫變換列表 ## 概述 `SVGAnimatedTransformList` 是一個用於SVG（可縮放矢量圖形）中的JavaScript介面，它允許開發者管理和操作SVG元素的變換列表，以實現動畫效果和動態修改。 #...
Meta Keywords: svganimatedtransformlist, baseval, let, rect, animval
-->

# SVGAnimatedTransformList：JavaScript 中的可動畫變換列表

## 概述
`SVGAnimatedTransformList` 是一個用於SVG（可縮放矢量圖形）中的JavaScript介面，它允許開發者管理和操作SVG元素的變換列表，以實現動畫效果和動態修改。

## 文件說明
`SVGAnimatedTransformList` 是一個專門用於SVG的API，包含一組變換（如平移、縮放和旋轉）的列表。它主要由兩部分組成：`baseVal` 和 `animVal`。`baseVal` 表示基本的變換列表，而 `animVal` 則表示當前動畫中的變換列表。

### 目的
`SVGAnimatedTransformList` 使得開發者能夠：
- 動態改變SVG元素的變換屬性。
- 創建複雜的動畫效果。
- 獲取和設置變換列表以便於操作。

### 用法
使用 `SVGAnimatedTransformList` 時，通常需要通過SVG元素的 `transform` 屬性來訪問。例如：

```javascript
let svgElement = document.getElementById('mySVGElement');
let transformList = svgElement.transform.baseVal;
```

### 詳細說明
- **屬性**：
  - `baseVal`：返回一個 `SVGTransformList` 對象，表示當前的基本變換。
  - `animVal`：返回當前動畫的變換列表，通常在動畫進行時會改變。

- **方法**：
  - `appendItem(newItem)`：將新的變換項目添加到列表的末尾。
  - `removeItem(index)`：移除指定索引的變換項目。
  - `replaceItem(newItem, index)`：用新的變換項目替換指定索引的項目。

## 示例
以下是如何使用 `SVGAnimatedTransformList` 的基本示例：

```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue" />
</svg>

<script>
  let rect = document.getElementById('myRect');
  let transformList = rect.transform.baseVal;

  // 添加平移變換
  let translate = rect.ownerSVGElement.createSVGTransform();
  translate.setTranslate(50, 50);
  transformList.appendItem(translate);

  // 添加旋轉變換
  let rotate = rect.ownerSVGElement.createSVGTransform();
  rotate.setRotate(45, 50, 50);
  transformList.appendItem(rotate);
</script>
```

## 解釋
使用 `SVGAnimatedTransformList` 時需注意以下幾點：
- 確保正確訪問 `SVGTransformList`，因為錯誤的索引會導致錯誤。
- 動畫期間 `animVal` 會改變，而 `baseVal` 則保持不變，這需要開發者在讀取時區分。
- 當使用 `appendItem` 時，新的變換將添加到列表的末尾，影響最終的變換效果。

## 總結
`SVGAnimatedTransformList` 是一個強大的工具，允許開發者在JavaScript中靈活地操作SVG元素的變換，以實現動態和動畫效果。