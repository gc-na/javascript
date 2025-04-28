<!--
Meta Description: # Uint16Array：JavaScript中的16位无符号整数数组 ## 概述 `Uint16Array` 是 JavaScript 中的一种类型化数组，用于表示无符号的 16 位整数。它允许在 JavaScript 中以高效的方式处理二进制数据，特别适用于需要存储和操作较大数值的场景。 ##...
Meta Keywords: uint16array, const, javascript, new, 100
-->

# Uint16Array：JavaScript中的16位无符号整数数组

## 概述
`Uint16Array` 是 JavaScript 中的一种类型化数组，用于表示无符号的 16 位整数。它允许在 JavaScript 中以高效的方式处理二进制数据，特别适用于需要存储和操作较大数值的场景。

## 文档
### 目的
`Uint16Array` 的主要目的是提供一种方法来存储和操作无符号 16 位整数，从而允许更低级别的二进制数据处理。由于其固定的大小，它在处理大量数据时效率更高。

### 用法
要创建一个 `Uint16Array`，可以使用以下几种方式：

1. **使用长度创建**: 
   ```javascript
   const arr = new Uint16Array(4); // 创建一个长度为 4 的 Uint16Array
   ```

2. **使用数组初始化**: 
   ```javascript
   const arr = new Uint16Array([1, 2, 3, 4]); // 使用数组初始化
   ```

3. **使用其他类型化数组或 ArrayBuffer**:
   ```javascript
   const buffer = new ArrayBuffer(8);
   const arr = new Uint16Array(buffer); // 从 ArrayBuffer 创建 Uint16Array
   ```

### 详细说明
- `Uint16Array` 的每个元素都占用 2 字节（16 位）。
- 该数组的索引从 0 开始，最大长度为 65536（2^16）。
- 在创建 `Uint16Array` 时，如果提供的值超出 0 到 65535 的范围，将会被截断。
- `Uint16Array` 支持多种方法，如 `set()`、`subarray()` 和 `fill()`，这些方法可以用于修改数组的内容。

## 示例
```javascript
// 创建一个 Uint16Array
const uint16 = new Uint16Array(5);
uint16[0] = 65535; // 最大值
uint16[1] = 30000;
console.log(uint16); // Uint16Array(5) [65535, 30000, 0, 0, 0]

// 从数组初始化
const initializedArray = new Uint16Array([1000, 2000, 3000]);
console.log(initializedArray); // Uint16Array(3) [1000, 2000, 3000]

// 使用 fill 方法
const filledArray = new Uint16Array(5).fill(100);
console.log(filledArray); // Uint16Array(5) [100, 100, 100, 100, 100]

// 使用 subarray 方法
const subArray = initializedArray.subarray(1, 3);
console.log(subArray); // Uint16Array(2) [2000, 3000]
```

## 解释
- **常见陷阱**: 使用 `Uint16Array` 时要注意，输入的负数会被转换为 0，超出范围的正数会被截断。例如，65536 将会变成 0。
- **性能注意**: 在处理大规模数据时，`Uint16Array` 提供了更好的内存管理和性能表现。
- **兼容性**: 确保运行环境支持 `TypedArray`，大多数现代浏览器都已支持。

## 一句话总结
`Uint16Array` 是 JavaScript 中用于存储和操作无符号 16 位整数的高效类型化数组。