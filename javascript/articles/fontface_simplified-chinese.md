<!--
Meta Description: # FontFace: JavaScript 字体加载与管理 ## 摘要 FontFace 是一个 JavaScript 接口，用于动态加载和管理网页中的字体，让开发者能够在应用中灵活使用自定义字体。 ## 文档 FontFace 接口允许开发者通过 JavaScript 创建和操作字体对象。它的主...
Meta Keywords: fontface, javascript, error, fontfamily, function
-->

# FontFace: JavaScript 字体加载与管理

## 摘要
FontFace 是一个 JavaScript 接口，用于动态加载和管理网页中的字体，让开发者能够在应用中灵活使用自定义字体。

## 文档
FontFace 接口允许开发者通过 JavaScript 创建和操作字体对象。它的主要目的是提供一种在运行时加载字体的方式，使得网页能够在没有预先加载的情况下使用自定义字体。

### 主要用途
- 动态加载字体文件
- 在网页中创建自定义字体
- 控制字体的样式、粗细、宽度等属性

### 使用方法
FontFace 构造函数的基本语法如下：
```javascript
let font = new FontFace(fontFamily, source, options);
```

- **fontFamily**: 字体的名称（字符串格式），在 CSS 中使用。
- **source**: 字体文件的 URL，可以是字符串或 ArrayBuffer。
- **options**: 可选的配置对象，包含字体的样式、粗细等属性。

### 加载字体
一旦创建了 FontFace 实例，可以使用 `load()` 方法来加载字体，并将其添加到文档中：
```javascript
font.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = fontFamily;
}).catch(function(error) {
    console.error('字体加载失败:', error);
});
```

## 示例
以下是使用 FontFace 的基本示例：

```javascript
// 创建 FontFace 实例
let myFont = new FontFace('MyCustomFont', 'url(/fonts/my-font.woff2)');

// 加载字体
myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont); // 将字体添加到文档中
    document.body.style.fontFamily = 'MyCustomFont'; // 应用字体
}).catch(function(error) {
    console.error('字体加载失败:', error);
});
```

## 说明
在使用 FontFace 时需要注意以下几点：
- **跨域问题**: 如果字体文件存储在不同的域名上，确保服务器提供了正确的 CORS headers，否则字体可能无法加载。
- **字体格式**: 确保提供的字体文件格式（如 WOFF、WOFF2、TTF等）被浏览器支持。
- **字体加载时间**: 动态加载字体可能会导致页面渲染延迟，确保在用户体验上进行平衡。

## 一句话总结
FontFace 是一个强大的接口，允许开发者在 JavaScript 中动态加载和管理自定义字体。