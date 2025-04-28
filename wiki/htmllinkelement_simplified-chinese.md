<!--
Meta Description: # HTMLLinkElement：JavaScript 中的 HTML 链接元素 ## 概述 `HTMLLinkElement` 是一个表示 HTML `<link>` 元素的接口，通常用于定义文档与外部资源（如样式表、预取链接等）之间的关系。它是 DOM（文档对象模型）的一部分，可以通过 Jav...
Meta Keywords: link, javascript, htmllinkelement, rel, document
-->

# HTMLLinkElement：JavaScript 中的 HTML 链接元素

## 概述
`HTMLLinkElement` 是一个表示 HTML `<link>` 元素的接口，通常用于定义文档与外部资源（如样式表、预取链接等）之间的关系。它是 DOM（文档对象模型）的一部分，可以通过 JavaScript 进行操作和管理。

## 文档
`HTMLLinkElement` 的主要用途是与文档的外部资源建立连接。这个接口提供了对 `<link>` 元素的访问和操作能力，允许开发者通过 JavaScript 读取或修改链接的属性。

### 属性
- **href**: 返回或设置链接的 URL。
- **rel**: 返回或设置链接与当前文档的关系。
- **type**: 返回或设置链接资源的 MIME 类型。
- **media**: 返回或设置链接的媒体查询。

### 方法
- **setAttribute()**: 设置指定属性的值。
- **getAttribute()**: 获取指定属性的值。

### 使用示例
可以通过以下方式创建和操作 `HTMLLinkElement`：

```javascript
// 创建一个新的链接元素
const link = document.createElement('link');

// 设置链接的属性
link.href = 'styles.css';
link.rel = 'stylesheet';
link.type = 'text/css';

// 将链接元素添加到文档的头部
document.head.appendChild(link);
```

## 示例
以下是一些基本用法示例：

### 添加样式表链接
```javascript
const link = document.createElement('link');
link.href = 'styles.css';
link.rel = 'stylesheet';
document.head.appendChild(link);
```

### 修改现有链接元素
```javascript
const existingLink = document.querySelector('link[rel="stylesheet"]');
existingLink.href = 'new-styles.css';
```

### 检查链接的关系
```javascript
const link = document.querySelector('link[rel="stylesheet"]');
console.log(link.rel); // 输出 "stylesheet"
```

## 说明
在使用 `HTMLLinkElement` 时，有几个常见的陷阱需要注意：

- **加载顺序**: 确保在文档的 `<head>` 部分添加链接元素，以便浏览器在渲染页面时能够正确加载样式。
- **媒体查询**: 使用 `media` 属性时，确保正确的媒体类型字符串，以避免样式不应用于特定设备。
- **跨域问题**: 当使用外部样式表时，检查 CORS 策略以确保资源能够正常加载。

## 一句话总结
`HTMLLinkElement` 是 JavaScript 中用于操作 HTML `<link>` 元素的接口，允许开发者动态管理文档与外部资源的关系。