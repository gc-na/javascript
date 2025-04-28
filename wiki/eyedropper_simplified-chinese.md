<!--
Meta Description: # EyeDropper: JavaScript 颜色选择器 API ## 概述 EyeDropper 是一个 JavaScript API，允许开发者创建一个用户友好的颜色选择器，让用户从屏幕上选取颜色。这个特性在网页设计和图形应用中非常有用，能够提升用户体验。 ## 文档 ### 目的 EyeD...
Meta Keywords: eyedropper, api, javascript, open, result
-->

# EyeDropper: JavaScript 颜色选择器 API

## 概述
EyeDropper 是一个 JavaScript API，允许开发者创建一个用户友好的颜色选择器，让用户从屏幕上选取颜色。这个特性在网页设计和图形应用中非常有用，能够提升用户体验。

## 文档
### 目的
EyeDropper API 主要用于获取用户所选颜色的 RGB 值。它允许用户通过点击屏幕上的任何位置来选择颜色，并将选中的颜色返回给开发者进行进一步处理。

### 用法
要使用 EyeDropper API，首先需要创建一个 EyeDropper 对象，然后调用它的 `open()` 方法。该方法返回一个包含用户选择的颜色信息的 Promise。

#### 创建 EyeDropper 实例
```javascript
const eyeDropper = new EyeDropper();
```

#### 打开颜色选择器
```javascript
eyeDropper.open().then(result => {
    console.log(result.sRGBHex); // 输出选中的颜色的十六进制值
}).catch(err => {
    console.error(err); // 处理错误
});
```

### 详细信息
- **Browser Compatibility**: EyeDropper API 目前在多个现代浏览器中均有支持，但在某些旧版浏览器中可能不兼容。
- **安全性**: 由于此 API 需要访问用户的屏幕内容，必须在 HTTPS 环境下使用。
- **权限**: 用户必须明确授权才能使用 EyeDropper API。

## 示例
### 基本使用示例
```javascript
// 创建 EyeDropper 实例
const eyeDropper = new EyeDropper();

// 打开颜色选择器
eyeDropper.open()
    .then(result => {
        // 处理选中的颜色
        const color = result.sRGBHex;
        console.log(`您选择的颜色是: ${color}`);
    })
    .catch(err => {
        console.error('选择颜色时发生错误:', err);
    });
```

## 解释
### 常见问题
- **不支持的浏览器**: 在不支持 EyeDropper API 的浏览器中调用 `open()` 方法会导致错误。确保在现代浏览器中进行测试。
- **HTTPS 限制**: EyeDropper API 仅在安全上下文中可用，因此请确保你的网页运行在 HTTPS 协议下。
- **用户授权**: 用户必须点击以允许访问颜色选择器，拒绝后将无法获取颜色信息。

## 一句总结
EyeDropper API 是一个强大的工具，使得用户可以轻松选择屏幕上的颜色，并在 JavaScript 中获取其值。