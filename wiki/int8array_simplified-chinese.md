<!--
Meta Description: # Int8Array：JavaScript 中的 8 位有符号整数数组 ## 概述 Int8Array 是 JavaScript 中的一种类型化数组，专门用于存储 8 位有符号整数。它允许高效地处理和存储二进制数据，特别适用于需要进行低级别数据处理的场景。 ## 文档 ### 目的 Int8Arr...
Meta Keywords: int8array, javascript, int8, new, 128
-->

# Int8Array：JavaScript 中的 8 位有符号整数数组

## 概述
Int8Array 是 JavaScript 中的一种类型化数组，专门用于存储 8 位有符号整数。它允许高效地处理和存储二进制数据，特别适用于需要进行低级别数据处理的场景。

## 文档

### 目的
Int8Array 提供了一种机制来创建、操作和访问 8 位有符号整数数组。每个元素的取值范围从 -128 到 127，适合处理小范围的整数数据。

### 用法
要创建一个 Int8Array，可以使用以下构造函数：

```javascript
new Int8Array(length);
```

- `length`：数组的长度，表示要创建的元素数量。

也可以通过传入一个数组或类数组对象来初始化 Int8Array：

```javascript
new Int8Array(array);
```

- `array`：可以是一个普通数组、另一个类型化数组或类数组对象。

### 详细信息
- **字节大小**：Int8Array 中的每个元素占用 1 个字节（8 位）。
- **方法**：Int8Array 支持基本的数组方法，例如 `set()`, `subarray()`, `fill()`, 和 `forEach()`。
- **视图**：Int8Array 可以与其他类型化数组（如 Uint8Array, Float32Array 等）共享同一内存缓冲区。

## 示例

### 创建 Int8Array
```javascript
let int8 = new Int8Array(5); // 创建一个长度为 5 的 Int8Array
console.log(int8); // 输出: Int8Array(5) [0, 0, 0, 0, 0]
```

### 初始化 Int8Array
```javascript
let array = new Int8Array([-128, 0, 127]);
console.log(array); // 输出: Int8Array(3) [-128, 0, 127]
```

### 使用 set 方法
```javascript
let int8 = new Int8Array(5);
int8.set([1, 2, 3]);
console.log(int8); // 输出: Int8Array(5) [1, 2, 3, 0, 0]
```

### 使用 forEach 方法
```javascript
let int8 = new Int8Array([1, 2, 3]);
int8.forEach((value) => {
    console.log(value); // 输出: 1 2 3
});
```

## 说明
- **常见陷阱**：使用超出 Int8Array 范围的值时，值会被截断。例如，如果尝试设置为 128，将会变为 -128。
- **性能注意**：与普通数组相比，类型化数组在处理大量数据时性能更好，因为它们在内存中是连续的。
- **缺少方法**：Int8Array 不支持所有普通数组的方法，例如 `push()` 和 `pop()`。

## 一句话总结
Int8Array 是 JavaScript 中用于处理 8 位有符号整数的高效类型化数组，适合低级别的数据操作。