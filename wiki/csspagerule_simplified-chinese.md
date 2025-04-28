<!--
Meta Description: # CSSPageRule：JavaScript 中的 CSS 页面规则 ## 简介 CSSPageRule 是 JavaScript 中用于操作 CSS 页面的规则对象。它允许开发者动态地修改样式表中的页面样式，如页面的格式和布局。 ## 文档 CSSPageRule 代表一个 CSS 页面的规则...
Meta Keywords: csspagerule, stylesheet, javascript, page, cssrules
-->

# CSSPageRule：JavaScript 中的 CSS 页面规则

## 简介
CSSPageRule 是 JavaScript 中用于操作 CSS 页面的规则对象。它允许开发者动态地修改样式表中的页面样式，如页面的格式和布局。

## 文档
CSSPageRule 代表一个 CSS 页面的规则，它由 `@page` 规则定义。此对象提供了对页面样式的访问和修改功能。通过 JavaScript，开发者可以添加、删除或更新页面样式，以适应打印或特定布局需求。

### 属性
- **selectorText**：获取或设置规则的选择器文本。
- **style**：返回与此规则相关的 CSSStyleDeclaration 对象，允许对样式属性进行读写。

### 方法
- **deleteRule()**：从样式表中删除此规则。
- **insertRule()**：在样式表的特定位置插入规则。

### 用法
CSSPageRule 通常与样式表（CSSStyleSheet）一起使用，开发者可以通过访问样式表的规则集合来获取并修改 CSSPageRule。

## 示例
以下是使用 CSSPageRule 的基本示例：

### 示例 1：访问现有的 @page 规则
```javascript
let styleSheet = document.styleSheets[0];
for (let i = 0; i < styleSheet.cssRules.length; i++) {
    if (styleSheet.cssRules[i] instanceof CSSPageRule) {
        console.log(styleSheet.cssRules[i].selectorText);  // 输出 @page
    }
}
```

### 示例 2：添加新的 @page 规则
```javascript
let styleSheet = document.styleSheets[0];
styleSheet.insertRule('@page { margin: 1in; }', styleSheet.cssRules.length);
```

### 示例 3：修改现有的 @page 规则
```javascript
let styleSheet = document.styleSheets[0];
for (let i = 0; i < styleSheet.cssRules.length; i++) {
    if (styleSheet.cssRules[i] instanceof CSSPageRule) {
        styleSheet.cssRules[i].style.margin = '2in';  // 修改边距
    }
}
```

## 解释
在使用 CSSPageRule 时，需要注意以下几点：
- **浏览器支持**：并非所有浏览器都支持 CSSPageRule，特别是在旧版浏览器中，可能会遇到兼容性问题。
- **动态修改影响**：动态添加或修改 @page 规则可能会影响打印样式，因此在进行这些操作时，需充分测试打印效果。
- **选择器文本**：selectorText 属性只能用于获取规则的选择器，尝试直接设置该属性会抛出错误。

## 一句话总结
CSSPageRule 是 JavaScript 中用于操作和修改 CSS 页面样式的对象。