<!--
Meta Description: # SVGFEDisplacementMapElement：JavaScript中的SVG位移映射元素 ## 简介 `SVGFEDisplacementMapElement` 是SVG（可缩放矢量图形）中用于创建位移效果的元素。在JavaScript中，我们可以通过DOM操作来访问和修改这个元素，从...
Meta Keywords: svgfedisplacementmapelement, svg, 400, filter, scale
-->

# SVGFEDisplacementMapElement：JavaScript中的SVG位移映射元素

## 简介
`SVGFEDisplacementMapElement` 是SVG（可缩放矢量图形）中用于创建位移效果的元素。在JavaScript中，我们可以通过DOM操作来访问和修改这个元素，从而实现丰富的图形效果。

## 文档
`SVGFEDisplacementMapElement` 继承自`SVGElement`，主要用于将图像的像素位移应用到其他图像上。它通常与滤镜效果结合使用，能够创造出各种艺术效果。

### 目的
`SVGFEDisplacementMapElement` 主要用于根据位移图（通常是灰度图像）来改变图像中每个像素的位置，通过设置不同的位移值，能够产生立体效果、波浪效果等。

### 用法
在JavaScript中，可以通过以下步骤使用 `SVGFEDisplacementMapElement`：

1. 创建 SVG 元素并将其添加到文档中。
2. 创建位移映射元素并设置其属性。
3. 将位移映射元素应用于所需的图形元素。

### 关键属性
- `in1`：指定输入图像的ID。
- `in2`：指定位移图的ID。
- `scale`：定义位移的强度。

## 示例
以下是一个基本的使用示例，展示如何在JavaScript中创建和使用 `SVGFEDisplacementMapElement`。

```html
<svg width="400" height="400">
  <defs>
    <filter id="displacementFilter">
      <feDisplacementMap in="SourceGraphic" in2="displacementMap" scale="20" />
    </filter>
    <image id="displacementMap" href="path/to/displacement-map.png" width="400" height="400" />
  </defs>
  <image id="sourceImage" href="path/to/source-image.jpg" width="400" height="400" filter="url(#displacementFilter)" />
</svg>
```

### JavaScript代码
```javascript
const svg = document.querySelector('svg');
const filter = svg.querySelector('#displacementFilter feDisplacementMap');
filter.setAttribute('scale', '30'); // 修改位移强度
```

## 说明
使用 `SVGFEDisplacementMapElement` 时，需注意以下几点：
- 位移图必须是灰度图像，黑色区域表示无位移，白色区域表示最大位移。
- 确保在使用位移映射之前，相关图像元素已加载完成。
- 过大的 `scale` 值可能导致图像失真，因此应根据实际需求进行调整。

## 一句话总结
`SVGFEDisplacementMapElement` 是一个用于在SVG中实现图像位移效果的元素，通过JavaScript可以动态调整其属性以创建丰富的视觉效果。