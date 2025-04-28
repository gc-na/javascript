<!--
Meta Description: # JavaScript中的NaN（非数字） ## 概述 NaN（Not-a-Number）是JavaScript中的一个特殊值，表示一个非数字值。它通常出现在数学运算或解析数值时，输入无法被转换为有效数字的情况下。 ## 文档 ### 目的 NaN用于指示一个计算结果不是有效的数字。这在处理数值时...
Meta Keywords: number, isnan, nan, parseint, abc
-->

# JavaScript中的NaN（非数字）

## 概述
NaN（Not-a-Number）是JavaScript中的一个特殊值，表示一个非数字值。它通常出现在数学运算或解析数值时，输入无法被转换为有效数字的情况下。

## 文档
### 目的
NaN用于指示一个计算结果不是有效的数字。这在处理数值时非常重要，尤其是在进行数学计算和数据验证时。

### 用法
NaN是JavaScript中的全局属性，属于Number对象。它的类型是“number”，但与任何数字都不相等，包括它自身。判断一个值是否为NaN，应该使用`Number.isNaN()`方法，而不是直接使用`===`运算符。

### 详细信息
- **类型**: `number`
- **唯一性**: NaN与任何值都不相等，包括NaN本身。要检查一个值是否为NaN，应该使用`Number.isNaN()`或`isNaN()`方法。
- **生成NaN的情况**:
  - 无法解析的字符串，例如`parseInt("abc")`。
  - 数学运算的错误，例如`Math.sqrt(-1)`。
  - 非法的数学运算，例如`0/0`。

## 示例
### 示例1: 使用`parseInt()`生成NaN
```javascript
let result = parseInt("abc");
console.log(result); // 输出: NaN
```

### 示例2: 使用`Math.sqrt()`生成NaN
```javascript
let sqrtResult = Math.sqrt(-1);
console.log(sqrtResult); // 输出: NaN
```

### 示例3: 检查NaN
```javascript
let value = NaN;
console.log(Number.isNaN(value)); // 输出: true
```

## 解释
- **常见问题**: 使用`==`或`===`来比较NaN会总是返回false。因此，不能依赖于直接比较来判断一个值是否为NaN。
- **gotchas**: 使用全局的`isNaN()`函数时，可能会得到意想不到的结果，因为它会尝试将输入转换为数字。例如，`isNaN("abc")`会返回true。

## 一句话总结
NaN是JavaScript中用于表示非数字值的特殊标识，常见于数学运算和数据解析错误。