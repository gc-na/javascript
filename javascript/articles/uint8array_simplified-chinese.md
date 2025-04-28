<!--
Meta Description: # Uint8Array：JavaScript 中的高效无符号 8 位整数数组 ## 概述 `Uint8Array` 是 JavaScript 中一种用于处理无符号 8 位整数的类型化数组。它允许在高性能的环境中高效存储和操作二进制数据，广泛应用于 Web API、图像处理以及音频处理等场景。 ##...
Meta Keywords: uint8array, uint8, new, javascript, arraybuffer
-->

# Uint8Array：JavaScript 中的高效无符号 8 位整数数组

## 概述
`Uint8Array` 是 JavaScript 中一种用于处理无符号 8 位整数的类型化数组。它允许在高性能的环境中高效存储和操作二进制数据，广泛应用于 Web API、图像处理以及音频处理等场景。

## 文档
### 目的
`Uint8Array` 提供了一种存储无符号整数（范围从 0 到 255）的数组结构，使开发者能够更高效地处理原始二进制数据。

### 用法
`Uint8Array` 可以通过多种方式创建：
1. **空数组**：`new Uint8Array(length)` 通过指定长度创建一个新的 `Uint8Array`，所有元素初始化为 0。
2. **从数组创建**：`new Uint8Array(array)` 从普通数组或类数组对象创建 `Uint8Array`。
3. **从 ArrayBuffer 创建**：`new Uint8Array(buffer)` 从现有的 `ArrayBuffer` 创建 `Uint8Array`，可指定偏移量和长度。

### 细节
- `Uint8Array` 的每个元素都是 8 位的无符号整数，存储范围为 0 到 255。
- `Uint8Array` 具有许多内置方法，例如 `set()`, `subarray()`, `slice()` 等，可用于操作数组数据。
- 它还支持常用的数组方法，如 `map()`, `forEach()`, `every()`, 和 `some()`。

## 示例
### 创建一个空的 Uint8Array
```javascript
const uint8 = new Uint8Array(5);
console.log(uint8); // 输出: Uint8Array(5) [0, 0, 0, 0, 0]
```

### 从普通数组创建 Uint8Array
```javascript
const arr = [1, 2, 3, 255];
const uint8 = new Uint8Array(arr);
console.log(uint8); // 输出: Uint8Array(4) [1, 2, 3, 255]
```

### 从 ArrayBuffer 创建 Uint8Array
```javascript
const buffer = new ArrayBuffer(8);
const uint8 = new Uint8Array(buffer);
uint8[0] = 10;
uint8[1] = 20;
console.log(uint8); // 输出: Uint8Array(8) [10, 20, 0, 0, 0, 0, 0, 0]
```

### 使用 set() 方法
```javascript
const uint8 = new Uint8Array(5);
uint8.set([1, 2, 3]);
console.log(uint8); // 输出: Uint8Array(5) [1, 2, 3, 0, 0]
```

## 说明
- **常见误区**：在使用 `Uint8Array` 时，开发者可能会忽略其元素的类型限制，尝试将超出范围的值（如 -1 或 256）赋给元素时，值会被截断，导致意外结果。
- **内存管理**：`Uint8Array` 是基于 `ArrayBuffer` 的，了解其与 `ArrayBuffer` 的关系能够更好地管理内存。

## 一句话总结
`Uint8Array` 是 JavaScript 中用于高效存储和操作无符号 8 位整数的类型化数组。