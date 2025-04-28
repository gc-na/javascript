<!--
Meta Description: # SVGAnimatedRect：JavaScript 中的可动画矩形 ## 简介 SVGAnimatedRect 是 SVG（可缩放矢量图形）中用于表示矩形的动画属性。在 JavaScript 中，它允许开发者动态地控制和动画化矩形的属性，为网页增添生动的视觉效果。 ## 文档 ### 目的 S...
Meta Keywords: svg, svganimatedrect, javascript, width, rect
-->

# SVGAnimatedRect：JavaScript 中的可动画矩形

## 简介
SVGAnimatedRect 是 SVG（可缩放矢量图形）中用于表示矩形的动画属性。在 JavaScript 中，它允许开发者动态地控制和动画化矩形的属性，为网页增添生动的视觉效果。

## 文档
### 目的
SVGAnimatedRect 对象使开发者能够访问和操作 SVG 矩形的动画属性。这些属性包括矩形的位置（x、y）、宽度（width）、高度（height）以及角半径（rx、ry），支持在不同的时间和条件下进行动画。

### 用法
SVGAnimatedRect 是一个属性，通常与 SVG 矩形元素 `<rect>` 一起使用。开发者可以通过 JavaScript 访问这些属性并进行修改，从而实现动画效果。

### 属性
- **baseVal**: 表示矩形的基础值，类型为 `DOMRect`。
- **animVal**: 表示矩形的当前动画值，类型为 `DOMRect`。

### 示例
```html
<svg width="200" height="200">
    <rect id="myRect" x="10" y="10" width="50" height="50" fill="blue" />
</svg>

<script>
    const rect = document.getElementById("myRect");
    const animRect = rect.getBBox(); // 获取矩形的边界框
    console.log(animRect); // 输出: {x: 10, y: 10, width: 50, height: 50}
    
    rect.setAttribute("width", "100"); // 动态修改宽度
</script>
```

## 说明
在使用 SVGAnimatedRect 时，开发者需要注意以下几点：
- 动画效果需要通过 CSS 或 JavaScript 结合 SVG 动画属性实现。
- 在某些情况下，矩形的动画可能不会立即反映在界面上，开发者需要确保调用更新的方法。
- 访问 animVal 属性时，需要确保动画已经开始并在播放中，否则可能返回不准确的值。

## 一句话总结
SVGAnimatedRect 是用于操作和动画化 SVG 矩形属性的 JavaScript 对象，增强了网页的交互性和视觉吸引力。