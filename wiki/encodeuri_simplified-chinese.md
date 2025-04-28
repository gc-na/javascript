<!--
Meta Description: # JavaScript中的encodeURI函数详解 ## 概述 `encodeURI` 是一个在JavaScript中用于对URI（统一资源标识符）进行编码的内置函数。它能够确保URI的有效性和可传输性，避免在网络传输中出现错误。 ## 文档 ### 目的 `encodeURI` 的主要目的是将...
Meta Keywords: encodeuri, uri, javascript, let, http
-->

# JavaScript中的encodeURI函数详解

## 概述
`encodeURI` 是一个在JavaScript中用于对URI（统一资源标识符）进行编码的内置函数。它能够确保URI的有效性和可传输性，避免在网络传输中出现错误。

## 文档
### 目的
`encodeURI` 的主要目的是将URI中某些字符转换为可安全传输的格式，确保URI能够在不同的网络环境中正确解析。

### 用法
`encodeURI` 的基本语法如下：

```javascript
encodeURI(uri)
```

- **参数**: 
  - `uri` (字符串): 需要编码的URI字符串。
  
- **返回值**: 
  - 返回一个经过编码的URI字符串，其中特殊字符被替换为百分号（%）后跟随两个十六进制数字的格式。

### 详情
- `encodeURI` 不会对如下字符进行编码，因为它们在URI中具有特殊含义：
  - `:`, `/`, `?`, `#`, `&`, `=` 和 `+`
- 它适用于完整的URI字符串，通常用于处理HTTP请求的URL。

## 示例
以下是`encodeURI`的基本用法示例：

```javascript
let uri = "http://example.com/?name=张三&age=25";
let encodedURI = encodeURI(uri);
console.log(encodedURI); // 输出: http://example.com/?name=%E5%BC%A0%E4%B8%89&age=25
```

在这个示例中，中文字符“张三”被编码为其对应的UTF-8格式。

## 说明
### 常见问题和注意事项
- `encodeURI` 不能用于编码URI的组成部分，比如查询参数。对于这些部分应该使用 `encodeURIComponent` 函数。
- 如果对已经编码的URI再次使用 `encodeURI`，可能会导致意想不到的结果。
- 确保在发送HTTP请求或处理URL时使用此函数，以避免URL中的非法字符。

## 一句话总结
`encodeURI` 是JavaScript中用于将URI字符串进行安全编码的函数，确保其在网络传输中有效。