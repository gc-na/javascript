<!--
Meta Description: # Int32Array：JavaScript 中的 32 位有符号整型数组 ## 概述 `Int32Array` 是 JavaScript 中的一种类型化数组，专门用于存储 32 位有符号整数。它允许高效地处理二进制数据，特别适合需要进行数值运算和数据存储的应用场景。 ## 文档 ### 目的 `...
Meta Keywords: int32array, javascript, let, new, subarray
-->

# Int32Array：JavaScript 中的 32 位有符号整型数组

## 概述
`Int32Array` 是 JavaScript 中的一种类型化数组，专门用于存储 32 位有符号整数。它允许高效地处理二进制数据，特别适合需要进行数值运算和数据存储的应用场景。

## 文档
### 目的
`Int32Array` 主要用于处理和存储二进制数据，能够以固定大小的内存块来管理 32 位整数数组。它提供了比普通数组更高效的存储和操作方式，尤其在处理大量数值数据时，性能提升显著。

### 用法
`Int32Array` 可以通过几种方式创建：
1. **从长度创建**：直接指定数组的长度。
   ```javascript
   let arr = new Int32Array(5); // 创建一个长度为 5 的 Int32Array
   ```

2. **从数组或类数组对象创建**：将现有数组的值复制到 `Int32Array` 中。
   ```javascript
   let arr = new Int32Array([1, 2, 3, 4, 5]); // 从数组创建 Int32Array
   ```

3. **从另一个类型化数组创建**：可以从其他类型化数组转换。
   ```javascript
   let typedArr = new Uint8Array([255, 254, 253]);
   let arr = new Int32Array(typedArr.buffer); // 从 Uint8Array 创建 Int32Array
   ```

### 细节
`Int32Array` 的每个元素占用 4 字节（32 位），其值范围为 -2,147,483,648 到 2,147,483,647。对 `Int32Array` 的操作包括索引访问、修改元素以及利用其内建方法（如 `set` 和 `subarray`）进行更复杂的数据处理。

- **属性**：
  - `length`：返回数组的长度。
  - `BYTES_PER_ELEMENT`：返回每个元素的字节大小（4）。

- **方法**：
  - `set(array, offset)`：从另一个数组或类数组对象中设置值。
  - `subarray(begin, end)`：返回新的 `Int32Array` 视图，表示原数组的一个子区间。

## 示例
```javascript
// 创建 Int32Array
let intArray = new Int32Array(3);
intArray[0] = 10;
intArray[1] = 20;
intArray[2] = 30;

console.log(intArray); // 输出: Int32Array(3) [10, 20, 30]

// 使用 set 方法
let newArray = new Int32Array(3);
newArray.set([100, 200, 300]);
console.log(newArray); // 输出: Int32Array(3) [100, 200, 300]

// 使用 subarray 方法
let subArray = intArray.subarray(1, 3);
console.log(subArray); // 输出: Int32Array(2) [20, 30]
```

## 解释
使用 `Int32Array` 时，开发者需要注意以下几点：
- **类型限制**：输入的值必须在 32 位有符号整数的范围内，否则会导致数据溢出。
- **内存管理**：类型化数组直接与内存交互，使用不当可能导致性能问题或内存泄漏。
- **浏览器支持**：确保目标浏览器支持 `TypedArray`，大多数现代浏览器均已支持。

## 一句话总结
`Int32Array` 是 JavaScript 中用于高效存储和操作 32 位有符号整数的类型化数组，适合数值密集型应用。