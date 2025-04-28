<!--
Meta Description: # CSSStyleSheet：JavaScript 中的样式表对象 ## 概述 CSSStyleSheet 是一个 JavaScript 接口，允许开发者以编程方式访问和操作文档中的 CSS 样式表。它提供了一系列方法和属性，使得动态修改样式变得简单而高效。 ## 文档 ### 目的 CSSSty...
Meta Keywords: css, stylesheet, javascript, cssstylesheet, cssrules
-->

# CSSStyleSheet：JavaScript 中的样式表对象

## 概述
CSSStyleSheet 是一个 JavaScript 接口，允许开发者以编程方式访问和操作文档中的 CSS 样式表。它提供了一系列方法和属性，使得动态修改样式变得简单而高效。

## 文档
### 目的
CSSStyleSheet 接口用于表示一个 CSS 样式表，提供对其规则和属性的访问。开发者可以通过该接口添加、删除或修改样式规则，从而实现动态的样式控制。

### 使用
在 JavaScript 中，CSSStyleSheet 对象通常通过 `document.styleSheets` 属性访问。此属性返回一个样式表集合，开发者可以通过索引引用特定的样式表。

### 详细信息
- **属性**：
  - `cssRules`：返回样式表中的所有 CSS 规则的列表。
  - `insertRule(rule, index)`：在指定索引处插入一个新的 CSS 规则。
  - `deleteRule(index)`：删除指定索引处的 CSS 规则。

- **方法**：
  - `addRule()`：在 IE 中使用的用于添加规则的方法（不推荐，已废弃）。

## 示例
### 基本用法
```javascript
// 获取第一个样式表
let stylesheet = document.styleSheets[0];

// 添加新的 CSS 规则
stylesheet.insertRule("body { background-color: lightblue; }", stylesheet.cssRules.length);

// 删除第一个 CSS 规则
stylesheet.deleteRule(0);
```

### 动态修改样式
```javascript
// 获取样式表
let stylesheet = document.styleSheets[0];

// 修改现有规则
if (stylesheet.cssRules.length > 0) {
    stylesheet.cssRules[0].style.color = "red";
}
```

## 解释
常见的问题包括：
- **跨域问题**：如果样式表来自不同的源，浏览器会阻止访问其规则，导致 `cssRules` 返回空。
- **规则索引**：在插入或删除规则时，确保索引值在有效范围内，超出范围会导致错误。
- **浏览器兼容性**：某些方法（如 `addRule`）在现代浏览器中已被弃用，建议使用 `insertRule`。

## 一句总结
CSSStyleSheet 是 JavaScript 中用于操作和管理 CSS 样式表的强大接口。