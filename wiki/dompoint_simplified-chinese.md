<!--
Meta Description: # DOMPoint：JavaScript 中的二维和三维坐标点 ## 概述 `DOMPoint` 是一个用于表示二维或三维空间中点的对象，广泛应用于图形和动画处理。它提供了一个简单的 API 来处理坐标点及其转换，使得在 Web 开发中操作图形变得更加容易。 ## 文档 ### 目的 `DOMPo...
Meta Keywords: dompoint, javascript, let, new, 默认值为
-->

# DOMPoint：JavaScript 中的二维和三维坐标点

## 概述
`DOMPoint` 是一个用于表示二维或三维空间中点的对象，广泛应用于图形和动画处理。它提供了一个简单的 API 来处理坐标点及其转换，使得在 Web 开发中操作图形变得更加容易。

## 文档
### 目的
`DOMPoint` 用于创建和操作表示坐标的点。它可以用于图形上下文、碰撞检测和动画等各种场景。

### 用法
`DOMPoint` 的构造函数可以使用以下方式创建点：

```javascript
let point = new DOMPoint(x, y, z, w);
```

- `x`：点在 x 轴上的坐标（默认值为 0）。
- `y`：点在 y 轴上的坐标（默认值为 0）。
- `z`：点在 z 轴上的坐标（默认值为 0），适用于三维场景。
- `w`：齐次坐标（默认值为 1），用于透视计算。

### 属性
- `x`：获取或设置点的 x 坐标。
- `y`：获取或设置点的 y 坐标。
- `z`：获取或设置点的 z 坐标。
- `w`：获取或设置点的齐次坐标。

### 方法
- `matrixTransform(matrix)`：使用给定的变换矩阵转换点的坐标，返回一个新的 `DOMPoint` 对象。

## 示例
### 创建一个 DOMPoint
```javascript
let point2D = new DOMPoint(10, 20); // 创建一个二维点
console.log(point2D); // 输出：DOMPoint {x: 10, y: 20, z: 0, w: 1}
```

### 转换坐标
```javascript
let point = new DOMPoint(1, 1);
let matrix = new DOMMatrix().rotate(90); // 创建一个旋转 90 度的矩阵
let transformedPoint = point.matrixTransform(matrix); // 转换点
console.log(transformedPoint); // 输出新的坐标
```

## 说明
在使用 `DOMPoint` 时，开发者需注意以下几点：
- `DOMPoint` 的 `z` 和 `w` 属性主要用于三维图形，若只处理二维场景，可忽略这两个属性。
- 使用 `matrixTransform` 方法时，确保传入有效的矩阵对象，以避免运行时错误。
- `DOMPoint` 对象是不可变的，调用方法不会修改原始点，而是返回一个新的点对象。

## 一句话总结
`DOMPoint` 是一个强大的 JavaScript 对象，用于表示和操作二维及三维空间中的坐标点。