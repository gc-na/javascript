<!--
Meta Description: # CSSStyleRule：JavaScript 中的 CSS 样式规则接口 ## 概述 `CSSStyleRule` 是一个接口，表示一条 CSS 样式规则。它用于访问和操作 CSS 样式表中的样式规则，允许开发者通过 JavaScript 动态修改网页的样式。 ## 文档 `CSSStyleR...
Meta Keywords: cssstylerule, css, rule, javascript, style
-->

# CSSStyleRule：JavaScript 中的 CSS 样式规则接口

## 概述
`CSSStyleRule` 是一个接口，表示一条 CSS 样式规则。它用于访问和操作 CSS 样式表中的样式规则，允许开发者通过 JavaScript 动态修改网页的样式。

## 文档
`CSSStyleRule` 接口继承自 `CSSRule`，代表一个 CSS 规则，通常由选择器和相应的声明块组成。它的主要用途是读取和修改 CSS 规则的属性。

### 主要属性和方法
- **selectorText**: 获取或设置此样式规则的选择器文本。
- **style**: 返回一个 `CSSStyleDeclaration` 对象，表示与该规则相关的所有 CSS 属性。
- **cssText**: 获取或设置整个规则的文本表示。

### 使用示例
以下是一些基本使用示例，展示如何使用 `CSSStyleRule` 接口：

```javascript
// 获取样式表
let stylesheet = document.styleSheets[0];

// 遍历样式规则
for (let i = 0; i < stylesheet.cssRules.length; i++) {
    let rule = stylesheet.cssRules[i];
    
    // 检查规则类型
    if (rule instanceof CSSStyleRule) {
        console.log(rule.selectorText); // 输出选择器文本
        console.log(rule.style.cssText); // 输出规则的 CSS 文本
    }
}

// 修改样式规则
if (rule instanceof CSSStyleRule) {
    rule.style.color = 'red'; // 将文本颜色改为红色
}
```

## 解释
在使用 `CSSStyleRule` 时，开发者可能会遇到一些常见的问题：

1. **跨域问题**: 访问外部样式表中的规则可能会因同源策略而失败。
2. **规则类型检查**: 确保在处理 `cssRules` 时检查规则类型，以避免运行时错误。
3. **动态更新**: 修改 `style` 属性会实时更新页面，但直接修改 `cssText` 可能会导致覆盖整个规则。

## 一句话总结
`CSSStyleRule` 是用于访问和操作 CSS 样式表中样式规则的 JavaScript 接口。