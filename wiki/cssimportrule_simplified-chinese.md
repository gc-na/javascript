<!--
Meta Description: # CSSImportRule：JavaScript中的CSS导入规则 ## 概述 CSSImportRule是JavaScript中用于表示CSS样式表中的@import规则的接口。它允许开发者通过脚本访问和操作样式表的导入规则，以实现动态样式管理。 ## 文档 ### 目的 CSSImportR...
Meta Keywords: cssrules, stylesheets, cssimportrule, stylesheet, import规则
-->

# CSSImportRule：JavaScript中的CSS导入规则

## 概述
CSSImportRule是JavaScript中用于表示CSS样式表中的@import规则的接口。它允许开发者通过脚本访问和操作样式表的导入规则，以实现动态样式管理。

## 文档
### 目的
CSSImportRule接口用于表示CSS文档中的@import规则。开发者可以使用此接口访问到被导入的样式表，并对其进行操作。

### 用法
CSSImportRule是通过CSSOM（CSS对象模型）获取的，通常是在处理样式表时使用。可以使用`styleSheet.cssRules`属性访问到CSS规则集合，其中包括CSSImportRule。

### 详细信息
- **类型**：CSSImportRule
- **属性**：
  - `href`：返回导入的样式表的URL。
  - `styleSheet`：返回被导入样式表的CSSStyleSheet对象。
  
- **方法**：没有特定的方法，主要用于访问属性。

## 示例
```javascript
// 获取文档的所有样式表
const styleSheets = document.styleSheets;

// 遍历每个样式表
for (let i = 0; i < styleSheets.length; i++) {
    const cssRules = styleSheets[i].cssRules;

    // 遍历每个规则
    for (let j = 0; j < cssRules.length; j++) {
        // 检查规则是否为CSSImportRule
        if (cssRules[j] instanceof CSSImportRule) {
            console.log('导入的样式表URL:', cssRules[j].href);
            console.log('导入的样式表:', cssRules[j].styleSheet);
        }
    }
}
```

## 说明
- **常见陷阱**：在访问CSSImportRule时，确保样式表的CORS（跨源资源共享）设置正确，否则可能会导致SecurityError。
- **注意事项**：CSSImportRule只在支持CSSOM的现代浏览器中可用，老旧浏览器可能不支持此特性。

## 一句话总结
CSSImportRule接口允许JavaScript开发者访问和操作CSS样式表中的@import规则。