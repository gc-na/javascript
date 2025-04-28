<!--
Meta Description: # JavaScript中的decodeURI函数详解 ## 概述 `decodeURI`是JavaScript中的一个全局函数，用于解码通过`encodeURI`编码的Uniform Resource Identifier（URI）。它能够将URI中的百分号编码转换为对应的字符，便于在Web应用中...
Meta Keywords: decodeuri, encodeuri, const, encodeduri, https
-->

# JavaScript中的decodeURI函数详解

## 概述
`decodeURI`是JavaScript中的一个全局函数，用于解码通过`encodeURI`编码的Uniform Resource Identifier（URI）。它能够将URI中的百分号编码转换为对应的字符，便于在Web应用中处理URL。

## 文档

### 目的
`decodeURI`的主要目的是将包含特殊字符的URI字符串转换回可读的形式，以便程序可以正确处理和显示这些字符。

### 用法
`decodeURI`函数的语法如下：
```javascript
decodeURI(uri)
```

- **参数**：
  - `uri`：必需。要解码的URI字符串。

- **返回值**：
  - 返回解码后的URI字符串。

### 注意事项
- `decodeURI`不会解码保留字符，如 `#`、`&`、`?` 等。如果这些字符在URI中已被编码，`decodeURI`将不会对它们进行解码。
- 在处理不合法的URI时，该函数可能会抛出`URIError`异常。

## 示例

### 基本用法
```javascript
// 编码一个URI
const encodedURI = encodeURI("https://example.com/?name=张三&age=25");
// 解码URI
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 输出: https://example.com/?name=张三&age=25
```

### 解码含有编码字符的URI
```javascript
const encodedURI = "https%3A%2F%2Fexample.com%2Fpath%3Fquery%3D%E7%BB%93%E6%9E%9C";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 输出: https://example.com/path?query=结果
```

## 解释
- **常见问题**：
  - 使用`decodeURI`解码未通过`encodeURI`编码的字符串时，可能会导致结果不符合预期，甚至抛出错误。
  - 处理包含保留字符的URI时，确保这些字符的正确性，以免影响解码过程。

- **注意事项**：
  - 如果需要解码包含保留字符的URI，考虑使用`decodeURIComponent`，它会解码所有的字符，包括保留字符。

## 一句话总结
`decodeURI`是JavaScript中用于解码经过`encodeURI`编码的URI字符串的全局函数。