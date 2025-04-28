<!--
Meta Description: # SVGAnimatedNumberList：JavaScript 中的動態數字列表 ## 概述 `SVGAnimatedNumberList` 是一個用於處理 SVG（可縮放矢量圖形）中動態數字列表的 JavaScript 接口。它允許開發者在動畫中使用數字列表，並能夠隨時更新這些值。 ## 文...
Meta Keywords: baseval, svganimatednumberlist, svg, animval, animatednumberlist
-->

# SVGAnimatedNumberList：JavaScript 中的動態數字列表

## 概述
`SVGAnimatedNumberList` 是一個用於處理 SVG（可縮放矢量圖形）中動態數字列表的 JavaScript 接口。它允許開發者在動畫中使用數字列表，並能夠隨時更新這些值。

## 文檔
### 目的
`SVGAnimatedNumberList` 主要用於 SVG 元素的屬性動畫，特別是涉及多個數字的情況。這個接口提供了對數字列表的動畫支持，讓開發者可以在 SVG 動畫中對數字進行流暢的過渡和變化。

### 使用方法
`SVGAnimatedNumberList` 包含兩個屬性：
- `baseVal`：表示動畫的基本值，這是動畫開始的數字列表。
- `animVal`：表示動畫的當前值，這是動畫進行時的數字列表。

這些屬性可以通過 JavaScript 訪問和修改，以影響 SVG 元素的外觀和行為。

#### 示例
```javascript
// 獲取 SVG 元素
const svgElement = document.getElementById('mySvgElement');

// 獲取 SVGAnimatedNumberList
const animatedNumberList = svgElement.getAttribute('points');

// 訪問 baseVal 和 animVal
console.log(animatedNumberList.baseVal); // 輸出基本值
console.log(animatedNumberList.animVal); // 輸出當前動畫值

// 更新 baseVal
animatedNumberList.baseVal = new SVGNumberList();
animatedNumberList.baseVal.appendItem(new SVGNumber(10));
animatedNumberList.baseVal.appendItem(new SVGNumber(20));
```

### 解釋
在使用 `SVGAnimatedNumberList` 時，有幾個常見的陷阱和注意事項：
- 確保在操作 `baseVal` 和 `animVal` 時，使用正確的方法來更新列表，例如使用 `appendItem` 和 `removeItem`。
- 當數字列表更新時，可能需要手動觸發重繪，特別是在大型動畫中。
- 當使用動畫時，`animVal` 的值會在動畫過程中變化，但 `baseVal` 的變化不會影響 `animVal`，除非動畫重新開始。

## 一句總結
`SVGAnimatedNumberList` 是一個強大的工具，用於在 JavaScript 中管理 SVG 動畫的數字列表。