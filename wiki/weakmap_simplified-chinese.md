<!--
Meta Description: # JavaScript WeakMap：深入了解弱映射的特性与用法 ## 摘要 WeakMap 是 JavaScript 中的一种数据结构，允许你以弱引用的方式存储键值对，从而在不影响垃圾回收的情况下管理内存。 ## 文档 WeakMap 是 ES6 引入的一个内置对象，用于存储键值对。WeakM...
Meta Keywords: weakmap, obj, javascript, key, has
-->

# JavaScript WeakMap：深入了解弱映射的特性与用法

## 摘要
WeakMap 是 JavaScript 中的一种数据结构，允许你以弱引用的方式存储键值对，从而在不影响垃圾回收的情况下管理内存。

## 文档
WeakMap 是 ES6 引入的一个内置对象，用于存储键值对。WeakMap 的一个显著特征是它的键是弱引用，这意味着如果没有其他引用指向WeakMap中的键，垃圾回收器会自动回收这些键。这使得 WeakMap 非常适合存储私有数据或配置信息，避免内存泄漏。

### 主要特点
- **键的类型**：WeakMap 只接受对象作为键，原始值（如字符串、数字等）无法作为键。
- **弱引用**：WeakMap 的键是弱引用，允许垃圾回收器在没有其他引用的情况下回收这些键。
- **无法遍历**：WeakMap 不能被迭代，因此不支持 `forEach` 或 `for...of` 循环等方法。

### 创建 WeakMap
可以通过 `new WeakMap()` 创建一个新的 WeakMap 实例。

```javascript
const weakMap = new WeakMap();
```

### 方法
- **set(key, value)**：设置键值对。
- **get(key)**：根据键获取对应的值。
- **has(key)**：检查 WeakMap 中是否存在某个键。
- **delete(key)**：删除指定的键值对。

## 示例
以下是使用 WeakMap 的基本示例：

```javascript
// 创建一个 WeakMap
const weakMap = new WeakMap();

// 创建一个对象作为键
let obj = { name: 'John' };

// 使用 set 方法添加键值对
weakMap.set(obj, '私有信息');

// 使用 get 方法获取值
console.log(weakMap.get(obj)); // 输出: '私有信息'

// 使用 has 方法检查键是否存在
console.log(weakMap.has(obj)); // 输出: true

// 使用 delete 方法删除键值对
weakMap.delete(obj);
console.log(weakMap.has(obj)); // 输出: false
```

## 解释
### 常见陷阱与注意事项
1. **键的类型限制**：WeakMap 的键必须是对象，不可使用原始类型（如字符串或数字）。如果尝试使用原始类型作为键，将会抛出错误。
2. **垃圾回收**：由于 WeakMap 的键是弱引用，如果没有其他引用指向该对象，则该对象会被垃圾回收。这意味着在使用 WeakMap 时，确保你仍然有其他引用指向该对象是很重要的。
3. **无法遍历**：WeakMap 不支持任何遍历方法，这可能会使得在某些场景下使用它变得不那么直观。需要在设计时考虑这一点。

## 一句话总结
WeakMap 是一种允许你使用弱引用存储对象作为键的 JavaScript 数据结构，适合用来管理私有数据和避免内存泄漏。