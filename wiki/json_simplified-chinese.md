<!--
Meta Description: # JSON：JavaScript中的数据交换格式 ## 概述 JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，易于人类阅读和编写，同时也易于机器解析和生成。它常用于在客户端和服务器之间传递结构化数据。 ## 文档 ### 目的 JSON的主要目的是以一种...
Meta Keywords: json, stringify, const, obj, name
-->

# JSON：JavaScript中的数据交换格式

## 概述
JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，易于人类阅读和编写，同时也易于机器解析和生成。它常用于在客户端和服务器之间传递结构化数据。

## 文档
### 目的
JSON的主要目的是以一种简单的格式来存储和传输数据，使得不同的编程语言和系统能够方便地进行数据交换。

### 用法
在JavaScript中，JSON提供了两个主要的方法：`JSON.stringify()`和`JSON.parse()`。

- `JSON.stringify(value)`：将JavaScript对象或值转换为JSON字符串。
- `JSON.parse(text)`：将JSON字符串转换回JavaScript对象。

### 详细信息
- JSON格式仅支持文本数据，所有的键必须是字符串，值可以是字符串、数字、布尔值、数组、对象或`null`。
- JSON的语法必须严格遵循，例如，字符串必须使用双引号包围。
- 与传统的XML相比，JSON格式更简洁，解析速度更快。

## 示例
以下是一些基本的JSON用法示例：

### 示例 1：将对象转换为JSON字符串
```javascript
const obj = {
    name: "小明",
    age: 25,
    isStudent: false
};

const jsonString = JSON.stringify(obj);
console.log(jsonString); // 输出: {"name":"小明","age":25,"isStudent":false}
```

### 示例 2：将JSON字符串转换为对象
```javascript
const jsonString = '{"name":"小红","age":22,"isStudent":true}';
const obj = JSON.parse(jsonString);
console.log(obj.name); // 输出: 小红
```

## 解释
### 常见陷阱和注意事项
1. **字符串格式**：JSON中的字符串必须用双引号包围，单引号会导致解析错误。
2. **保留字**：JSON不支持函数和日期对象等JavaScript特有的数据类型。
3. **空值处理**：在JSON中，`undefined`会被忽略，而`null`会被保留。
4. **循环引用**：JSON.stringify()无法处理循环引用的对象，会抛出错误。
   
了解这些常见问题有助于避免在使用JSON时遇到的错误。

## 一句话总结
JSON是一种轻量级的数据交换格式，广泛用于JavaScript中对象和数据的表示与传输。