<!--
Meta Description: # CSSFontFaceRule 在 JavaScript 中的使用 ## 摘要 CSSFontFaceRule 是一个用于表示 CSS @font-face 规则的接口，允许开发者通过 JavaScript 动态操作和管理网页中的自定义字体。 ## 文档 ### 目的 CSSFontFaceRu...
Meta Keywords: cssfontfacerule, font, javascript, face, stylesheet
-->

# CSSFontFaceRule 在 JavaScript 中的使用

## 摘要
CSSFontFaceRule 是一个用于表示 CSS @font-face 规则的接口，允许开发者通过 JavaScript 动态操作和管理网页中的自定义字体。

## 文档
### 目的
CSSFontFaceRule 接口提供了一种方式来访问和修改 @font-face 规则，使得开发者能够根据需要动态地调整网页中的字体样式。

### 用法
CSSFontFaceRule 是 CSS 规则的一部分，主要用于定义网页中使用的字体。通过 JavaScript，开发者可以获取这些规则并进行更新或删除操作。

#### 属性
- `style`: 获取 CSSFontFaceRule 的 CSSStyleDeclaration 对象，允许对字体的样式进行更改。
- `fontFamily`: 获取或设置字体的名称。
- `src`: 获取或设置字体的来源，通常是一个 URL。
- `unicodeRange`: 获取或设置字体的 Unicode 范围。

### 详细信息
CSSFontFaceRule 是 CSSRule 接口的子类，支持 @font-face 规则的相关操作。使用 JavaScript 访问 CSSFontFaceRule 的实例通常需要借助 CSSStyleSheet 接口来获取样式表中的规则。

## 示例
### 基本用法
```javascript
// 获取样式表
const styleSheet = document.styleSheets[0];

// 遍历样式表中的规则
for (let i = 0; i < styleSheet.cssRules.length; i++) {
    const rule = styleSheet.cssRules[i];

    // 检查是否为 CSSFontFaceRule
    if (rule instanceof CSSFontFaceRule) {
        console.log(rule.fontFamily); // 输出字体名称
        console.log(rule.src); // 输出字体来源
    }
}

// 动态添加新的字体规则
const newFontFace = `@font-face {
    font-family: 'MyCustomFont';
    src: url('my-custom-font.woff2') format('woff2');
}`;
styleSheet.insertRule(newFontFace, styleSheet.cssRules.length);
```

## 解释
### 常见问题
- **获取规则失败**: 确保你访问的样式表确实包含 @font-face 规则，且没有跨域问题。
- **动态修改无效**: 若修改后的规则未反映在页面上，请检查样式表的优先级和其他 CSS 规则的影响。
- **浏览器支持**: CSSFontFaceRule 在现代浏览器中得到良好支持，但请确认兼容性。

## 一句话总结
CSSFontFaceRule 允许开发者通过 JavaScript 动态管理网页中的 @font-face 字体规则。