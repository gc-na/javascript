<!--
Meta Description: # CSSSupportsRule：JavaScript 中的 CSS 支持规则 ## 概述 CSSSupportsRule 是一种用于检测浏览器是否支持特定 CSS 特性的规则，通常结合 JavaScript 使用，以便根据浏览器的支持情况动态调整样式。 ## 文档 ### 目的 CSSSuppo...
Meta Keywords: css, javascript, supports, csssupportsrule, grid
-->

# CSSSupportsRule：JavaScript 中的 CSS 支持规则

## 概述
CSSSupportsRule 是一种用于检测浏览器是否支持特定 CSS 特性的规则，通常结合 JavaScript 使用，以便根据浏览器的支持情况动态调整样式。

## 文档
### 目的
CSSSupportsRule 提供了一种方式来检查浏览器是否支持某种 CSS 特性。通过结合 JavaScript，可以在运行时根据不同浏览器的能力调整页面样式，提高兼容性和用户体验。

### 用法
CSSSupportsRule 通常用在 CSS 中，与 @supports 规则结合使用。以下是基本的语法：

```css
@supports (property: value) {
    /* 如果支持该属性的值 */
}
```

在 JavaScript 中，可以使用 `CSS.supports()` 方法来检查支持情况：

```javascript
if (CSS.supports('property', 'value')) {
    // 该属性值被支持
}
```

### 细节
- CSSSupportsRule 可以嵌套使用，以便检测多个属性和条件。
- 支持的条件包括单个属性值、多个属性值的组合（使用 `and` 和 `or`），以及否定条件（使用 `not`）。
- 此功能在现代浏览器中广泛支持，但在一些旧版浏览器中可能不被支持。

## 示例
以下是一些简单的使用示例：

### 示例 1：基本检测
```css
@supports (display: grid) {
    .grid-container {
        display: grid;
    }
}
```

### 示例 2：结合 JavaScript 使用
```javascript
if (CSS.supports('display', 'grid')) {
    console.log('浏览器支持 Grid 布局');
} else {
    console.log('浏览器不支持 Grid 布局');
}
```

### 示例 3：多条件检查
```css
@supports (display: flex) and (flex-direction: column) {
    .flex-container {
        display: flex;
        flex-direction: column;
    }
}
```

## 说明
- 常见问题：确保使用的属性和值在目标浏览器中是有效的。某些新特性在旧版浏览器中可能无法使用。
- 陷阱：使用不支持的条件时，可能会导致样式不生效。因此，务必测试不同的浏览器环境。
- 性能注意：频繁检查支持可能会影响性能，建议在页面加载时进行检测。

## 一句话总结
CSSSupportsRule 是用于检测浏览器对特定 CSS 特性的支持的一种工具，结合 JavaScript 可以实现更加灵活的样式控制。