<!--
Meta Description: # DOMPointReadOnly：JavaScript中的只读点对象 ## 概述 `DOMPointReadOnly` 是 Web API 中的一部分，它表示一个不可变的二维或三维坐标点。这种对象主要用于图形和几何计算，特别是在处理 Canvas 或 SVG 图形时。由于其只读特性，`DOMPo...
Meta Keywords: dompointreadonly, 默认为, console, log, point2d
-->

# DOMPointReadOnly：JavaScript中的只读点对象

## 概述
`DOMPointReadOnly` 是 Web API 中的一部分，它表示一个不可变的二维或三维坐标点。这种对象主要用于图形和几何计算，特别是在处理 Canvas 或 SVG 图形时。由于其只读特性，`DOMPointReadOnly` 确保了点的坐标在创建后不会被修改。

## 文档
`DOMPointReadOnly` 的构造函数用于创建一个表示点的对象。该对象包含 x、y（以及可选的 z 和 w）坐标，通过这些坐标可以在二维或三维空间中精确定位。

### 目的
`DOMPointReadOnly` 提供了一种简单而有效的方式来处理和表示坐标点，尤其是在需要进行几何运算时。

### 用法
`DOMPointReadOnly` 通过构造函数创建，接受以下参数：

- `x` (可选): 点的 x 坐标，默认为 0。
- `y` (可选): 点的 y 坐标，默认为 0。
- `z` (可选): 点的 z 坐标，默认为 0（用于三维空间）。
- `w` (可选): 点的 w 坐标，默认为 1（用于齐次坐标）。

#### 示例代码
```javascript
// 创建一个二维点
const point2D = new DOMPointReadOnly(10, 20);
console.log(point2D.x); // 输出: 10
console.log(point2D.y); // 输出: 20

// 创建一个三维点
const point3D = new DOMPointReadOnly(10, 20, 30);
console.log(point3D.z); // 输出: 30
console.log(point3D.w); // 输出: 1
```

## 解释
使用 `DOMPointReadOnly` 时，需要注意以下几点：

1. **不可变性**：`DOMPointReadOnly` 对象创建后，其坐标值不能被修改。如果尝试更改其属性，将会导致 TypeError。
   
2. **用途场景**：该对象通常与 Canvas 和 WebGL 结合使用，方便进行图形绘制和变换。

3. **与其他对象的兼容性**：`DOMPointReadOnly` 可以与 `DOMPoint` 配合使用，后者是可变的点对象。在需要更改位置时，可以使用 `DOMPoint`，而在需要稳定状态时则使用 `DOMPointReadOnly`。

## 一句话总结
`DOMPointReadOnly` 是一个用于表示不可变的二维或三维坐标点的对象，适用于图形计算和绘制。