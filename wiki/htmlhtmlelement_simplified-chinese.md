<!--
Meta Description: # HTMLHtmlElement: JavaScript 中的 HTML 根元素 ## 简介 `HTMLHtmlElement` 是 JavaScript 中表示 HTML 文档根元素 `<html>` 的接口。它允许开发者访问和操作文档的根属性和方法，是构建和修改网页的重要组成部分。 ## 文档...
Meta Keywords: htmlhtmlelement, html, lang, javascript, htmlelement
-->

# HTMLHtmlElement: JavaScript 中的 HTML 根元素

## 简介
`HTMLHtmlElement` 是 JavaScript 中表示 HTML 文档根元素 `<html>` 的接口。它允许开发者访问和操作文档的根属性和方法，是构建和修改网页的重要组成部分。

## 文档
`HTMLHtmlElement` 继承自 `HTMLElement` 接口，提供了与 HTML 文档根相关的特定属性和方法。该元素通常是网页的起始点，包含所有其他 HTML 元素。

### 目的
`HTMLHtmlElement` 主要用于：
- 访问和操作 `<html>` 标签的属性（如 `lang`）。
- 控制文档元数据，例如设置语言和字符编码。

### 用法
在 JavaScript 中，可以通过 `document.documentElement` 访问当前文档的 `HTMLHtmlElement` 实例。以下是一些常用属性：
- `lang`：返回或设置文档的语言代码。
- `xmlns`：返回或设置 XML 命名空间。

### 详细信息
`HTMLHtmlElement` 的实例通常不需要创建，因为它是由浏览器自动生成的。开发者可以直接与其属性交互。例如，您可以使用以下代码来修改语言属性：

```javascript
document.documentElement.lang = "zh-CN"; // 设置文档语言为简体中文
```

## 示例
以下是使用 `HTMLHtmlElement` 的基本示例：

```javascript
// 获取 HTML 根元素
const htmlElement = document.documentElement;

// 输出当前文档的语言
console.log(htmlElement.lang); // 可能输出 "en"

// 修改语言属性
htmlElement.lang = "fr"; // 将语言设置为法语
console.log(htmlElement.lang); // 输出 "fr"
```

## 说明
在使用 `HTMLHtmlElement` 时，注意以下几点：
- 确保在文档加载完成后访问 `document.documentElement`，以避免获取到未定义的元素。
- 更改 `lang` 属性后，可能会影响搜索引擎优化（SEO）和页面的可访问性，因此请谨慎设置。

## 一句话总结
`HTMLHtmlElement` 在 JavaScript 中代表 HTML 文档的根元素，允许开发者访问和修改文档的基本属性。