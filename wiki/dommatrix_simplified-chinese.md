<!--
Meta Description: # DOMMatrix：JavaScript 中的矩阵操作 ## 概述 `DOMMatrix` 是一个用于表示和操作 2D 或 3D 矩阵的 JavaScript 接口。它在图形变换中非常有用，尤其是在处理平移、旋转、缩放和倾斜等变换时。 ## 文档 ### 目的 `DOMMatrix` 提供了一种...
Meta Keywords: dommatrix, javascript, let, matrix, new
-->

# DOMMatrix：JavaScript 中的矩阵操作

## 概述
`DOMMatrix` 是一个用于表示和操作 2D 或 3D 矩阵的 JavaScript 接口。它在图形变换中非常有用，尤其是在处理平移、旋转、缩放和倾斜等变换时。

## 文档
### 目的
`DOMMatrix` 提供了一种简单的方法来创建和操作矩阵，允许开发者在 Web 应用程序中实现复杂的图形效果。它是 Web 标准的一部分，支持广泛的浏览器。

### 用法
`DOMMatrix` 可以通过构造函数创建新的矩阵实例。可以通过传递数组、字符串或其他 `DOMMatrix` 实例来初始化矩阵。以下是基本的构造函数：

```javascript
let matrix = new DOMMatrix([a, b, c, d, e, f]);
```

- `a`、`b`、`c`、`d`、`e`、`f` 是矩阵的参数，分别代表：
  - `a`：水平缩放
  - `b`：水平倾斜
  - `c`：垂直倾斜
  - `d`：垂直缩放
  - `e`：水平位移
  - `f`：垂直位移

### 属性和方法
- **属性**：
  - `is2D`：返回布尔值，指示矩阵是否为 2D 矩阵。
  - `isIdentity`：返回布尔值，指示矩阵是否为单位矩阵。

- **方法**：
  - `invertSelf()`：就地反转矩阵。
  - `multiplySelf()`：以当前矩阵为基础，乘以另一个矩阵。
  - `rotateSelf()`：就地旋转矩阵。
  - `scaleSelf()`：就地缩放矩阵。
  - `translateSelf()`：就地平移矩阵。

## 示例
### 创建 2D 矩阵
```javascript
let matrix = new DOMMatrix([1, 0, 0, 1, 0, 0]); // 单位矩阵
```

### 旋转矩阵
```javascript
let matrix = new DOMMatrix();
matrix.rotateSelf(45); // 将矩阵旋转 45 度
console.log(matrix);
```

### 矩阵相乘
```javascript
let matrix1 = new DOMMatrix().translateSelf(100, 50);
let matrix2 = new DOMMatrix().scaleSelf(2, 2);
let resultMatrix = matrix1.multiplySelf(matrix2);
console.log(resultMatrix);
```

## 说明
使用 `DOMMatrix` 时，需注意以下几点：
- **性能问题**：频繁的矩阵操作可能会影响性能，尽量避免在动画循环中重复创建矩阵。
- **不可变性**：大多数方法（如 `rotateSelf()` 和 `scaleSelf()`）都是就地方法，直接修改当前矩阵。使用前请确保理解这一点。
- **兼容性**：确保目标浏览器支持 `DOMMatrix`，可以使用 `window.DOMMatrix` 检查。

## 一句话总结
`DOMMatrix` 是一个强大的 JavaScript 接口，用于创建和操作 2D 和 3D 矩阵，支持图形变换的各种需求。