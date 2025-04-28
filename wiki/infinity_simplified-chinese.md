<!--
Meta Description: # JavaScript中的无穷大（Infinity）概述 ## 概述 在JavaScript中，无穷大（Infinity）是一个表示正无穷大的特殊数值。它是一个全局属性，可以用于表示超出可表示数值范围的情况。 ## 文档 无穷大（Infinity）是JavaScript中的一个全局常量，表示一个超...
Meta Keywords: infinity, let, number, max, 无穷大
-->

# JavaScript中的无穷大（Infinity）概述

## 概述
在JavaScript中，无穷大（Infinity）是一个表示正无穷大的特殊数值。它是一个全局属性，可以用于表示超出可表示数值范围的情况。

## 文档
无穷大（Infinity）是JavaScript中的一个全局常量，表示一个超出数值范围的值。它的值为正无穷大，通常在数学计算中使用。无穷大是一个 Number 类型的值，可以与其他数值进行比较和运算。

### 用法
无穷大的使用非常简单，您可以直接通过 `Infinity` 来访问它。可以用于以下场景：
- 表示超出最大数值范围的值。
- 用于数学计算，例如除以零。
- 在算法中作为初始值，例如查找最小值或最大值。

### 详细信息
- **类型**：`Number`
- **值**：`Infinity`
- **比较**：
  - `Infinity > 1000` 返回 `true`
  - `Infinity === Infinity` 返回 `true`
  - `Infinity * 2` 返回 `Infinity`
- **与其他数值的运算**：
  - `Infinity + 1` 返回 `Infinity`
  - `Infinity - Infinity` 返回 `NaN`（不是一个数字）
  - `Infinity / 2` 返回 `Infinity`

## 示例
### 示例1：使用无穷大作为比较
```javascript
let a = 1000;
let b = Infinity;

console.log(a < b); // 输出: true
```

### 示例2：与数学运算结合
```javascript
let result = 1 / 0;
console.log(result); // 输出: Infinity
```

### 示例3：无穷大在算法中的应用
```javascript
let numbers = [10, 20, 30, 40, 50];
let max = -Infinity;

for (let number of numbers) {
    if (number > max) {
        max = number;
    }
}

console.log(max); // 输出: 50
```

## 说明
- **常见误区**：无穷大并不等于任何数字，包括自身的负值（-Infinity），在进行比较时应注意。
- **运算陷阱**：任何非数值与无穷大的运算结果通常是无穷大或NaN。例如，`Infinity - Infinity`会返回NaN，可能会导致逻辑错误。

## 一句话总结
无穷大（Infinity）是JavaScript中表示超出数值范围的特殊数值，常用于数学计算和算法初始化。