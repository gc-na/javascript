<!--
Meta Description: # JavaScript中的Set：集合数据结构的全面指南 ## 概述 在JavaScript中，`Set`是一种内置的数据结构，用于存储唯一值的集合。它可以存放任何类型的值，包括基本类型和引用类型。`Set`提供了高效的值查重和数据操作功能，是处理需要去重的数据集合的理想选择。 ## 文档 ###...
Meta Keywords: set, numbers, add, console, log
-->

# JavaScript中的Set：集合数据结构的全面指南

## 概述
在JavaScript中，`Set`是一种内置的数据结构，用于存储唯一值的集合。它可以存放任何类型的值，包括基本类型和引用类型。`Set`提供了高效的值查重和数据操作功能，是处理需要去重的数据集合的理想选择。

## 文档
### 目的
`Set`对象用于存储唯一值，允许对数据进行高效的添加、删除和查找操作。它与数组的主要区别在于，`Set`中的每个值只能出现一次，自动去重。

### 用法
使用`Set`非常简单。可以通过以下方式创建一个新的`Set`：

```javascript
const mySet = new Set();
```

可以通过`add()`方法向`Set`中添加值，使用`delete()`方法删除值，使用`has()`方法检查值是否存在，使用`clear()`方法清空`Set`。

### 详细信息
- **构造函数**：`Set`可以通过空构造函数创建，也可以接受一个可迭代对象（如数组）作为参数来初始化。
- **属性**：
  - `size`: 返回`Set`中值的数量。
- **方法**：
  - `add(value)`: 向`Set`添加一个新值。
  - `delete(value)`: 删除`Set`中的指定值。
  - `has(value)`: 检查`Set`中是否存在指定值，返回布尔值。
  - `clear()`: 清空`Set`中的所有值。
  - `forEach(callback)`: 对`Set`中的每个值执行给定的回调函数。

## 示例
```javascript
// 创建一个新的Set
const numbers = new Set();

// 添加值
numbers.add(1);
numbers.add(2);
numbers.add(2); // 重复值不会被添加

console.log(numbers); // 输出: Set { 1, 2 }

// 检查值是否存在
console.log(numbers.has(1)); // 输出: true
console.log(numbers.has(3)); // 输出: false

// 删除值
numbers.delete(1);
console.log(numbers); // 输出: Set { 2 }

// 清空Set
numbers.clear();
console.log(numbers.size); // 输出: 0
```

## 说明
在使用`Set`时，有几个常见的注意事项：
- `Set`会自动去重，因此即使多次添加相同的值，最终也只会保留一个实例。
- `Set`中的值是按插入顺序进行迭代的。
- 由于`Set`的值是基于引用的，因此对于对象类型的值，只有当引用相同时才被认为是相等的。

## 一句话总结
`Set`是JavaScript中的一种高效的数据结构，用于存储唯一值，支持快速的插入、删除和查找操作。