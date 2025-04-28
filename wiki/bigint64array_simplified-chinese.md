<!--
Meta Description: # BigInt64Array：JavaScript中的大整数数组 ## 概述 `BigInt64Array` 是 JavaScript 中的一种类型化数组，专门用于表示和操作 64 位带符号整数。它允许高效存储和处理大整数，适用于需要精确数值计算的场景。 ## 文档 `BigInt64Array`...
Meta Keywords: bigint64array, arr, javascript, const, new
-->

# BigInt64Array：JavaScript中的大整数数组

## 概述
`BigInt64Array` 是 JavaScript 中的一种类型化数组，专门用于表示和操作 64 位带符号整数。它允许高效存储和处理大整数，适用于需要精确数值计算的场景。

## 文档
`BigInt64Array` 是一种内置的类型化数组，存储以 64 位整数形式的值。它提供了一种高效的方式来处理大量的数字数据，尤其是在需要处理大于 `Number.MAX_SAFE_INTEGER` （即 2^53 - 1） 的整数时。

### 创建 BigInt64Array
可以通过以下几种方式创建 `BigInt64Array`：
1. **通过长度**：创建一个指定长度的数组，初始值为 0。
   ```javascript
   const arr = new BigInt64Array(5);
   ```
   
2. **通过数组**：用现有的数组或类数组对象初始化。
   ```javascript
   const arr = new BigInt64Array([1n, 2n, 3n]);
   ```
   
3. **通过 ArrayBuffer**：使用 `ArrayBuffer` 来初始化。
   ```javascript
   const buffer = new ArrayBuffer(8);
   const arr = new BigInt64Array(buffer);
   ```

### 特性
- **元素类型**：每个元素都是一个 64 位的带符号整数。
- **内存效率**：适合处理大量数字数据，避免了普通数组的开销。
- **支持方法**：提供了常见的数组方法如 `.set()`, `.subarray()`, `.slice()` 和 `.map()`。

## 示例
```javascript
// 创建 BigInt64Array
const arr = new BigInt64Array([100n, 200n, 300n]);

// 访问元素
console.log(arr[0]); // 输出 100n

// 修改元素
arr[1] = 250n;
console.log(arr[1]); // 输出 250n

// 使用 set() 方法
const newArr = new BigInt64Array(2);
newArr.set([400n, 500n]);
console.log(newArr); // 输出 BigInt64Array(2) [ 400n, 500n ]
```

## 说明
- **常见问题**：
  - `BigInt64Array` 只能存储 `BigInt` 类型的数字，尝试存储普通数字会导致类型转换错误。
  - 在与其他类型化数组（如 `Int32Array` 或 `Float64Array`）进行操作时，需要小心类型不匹配的问题。
  
- **性能**：由于 `BigInt64Array` 是类型化数组，操作速度较普通数组快，尤其是在处理大数据集时。

## 一句话总结
`BigInt64Array` 是 JavaScript 中用于高效存储和操作 64 位带符号整数的类型化数组。