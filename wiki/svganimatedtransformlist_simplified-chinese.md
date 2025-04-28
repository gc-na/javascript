<!--
Meta Description: # SVGAnimatedTransformList 在 JavaScript 中的使用 ## 概述 `SVGAnimatedTransformList` 是一个用于处理 SVG 图形中变换属性的 JavaScript 接口。该接口允许开发者对 SVG 图形的变换（如平移、旋转、缩放等）进行动画处理...
Meta Keywords: svg, svganimatedtransformlist, baseval, animval, svgtransformlist
-->

# SVGAnimatedTransformList 在 JavaScript 中的使用

## 概述
`SVGAnimatedTransformList` 是一个用于处理 SVG 图形中变换属性的 JavaScript 接口。该接口允许开发者对 SVG 图形的变换（如平移、旋转、缩放等）进行动画处理。

## 文档
`SVGAnimatedTransformList` 接口主要用于表示 SVG 元素的变换属性，提供了对变换列表的访问和修改。它包含两个属性：

- `baseVal`：表示基础变换列表，类型为 `SVGTransformList`。
- `animVal`：表示当前动画变换列表，类型为 `SVGTransformList`。

### 目的
通过使用 `SVGAnimatedTransformList`，开发者可以创建动态和交互式的 SVG 图形，使其能够根据用户的输入或其他条件进行变换。

### 用法
要使用 `SVGAnimatedTransformList`，你首先需要获取 SVG 元素的变换属性。通过访问该属性，你可以读取和修改 `baseVal` 和 `animVal`。

### 细节
- `baseVal` 是一个不可变的 `SVGTransformList`，表示元素的初始变换。
- `animVal` 是一个可变的 `SVGTransformList`，表示正在进行的动画变换。
- 通过使用 `SVGTransform` 对象，开发者可以添加、移除或修改变换。

## 示例
以下是一个简单的示例，演示如何使用 `SVGAnimatedTransformList` 来实现一个简单的旋转动画。

```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue" />
</svg>

<script>
  const rect = document.getElementById('myRect');
  const transformList = rect.transform.baseVal;

  // 创建一个旋转变换
  const rotateTransform = rect.ownerSVGElement.createSVGTransform();
  rotateTransform.setRotate(45, 50, 50); // 旋转45度，围绕(50, 50)

  // 将旋转变换添加到变换列表
  transformList.appendItem(rotateTransform);
</script>
```

## 说明
- 注意 `baseVal` 和 `animVal` 之间的区别，确保在动画过程中正确使用它们。
- 修改 `baseVal` 不会影响 `animVal`，反之亦然。
- 在进行复杂的动画时，过多的变换可能导致性能问题，因此应尽量优化变换列表。

## 一句话总结
`SVGAnimatedTransformList` 是一个强大的接口，用于在 JavaScript 中动态处理 SVG 元素的变换动画。