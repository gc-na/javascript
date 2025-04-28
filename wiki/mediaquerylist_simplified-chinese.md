<!--
Meta Description: # MediaQueryList - JavaScript 媒体查询列表详解 ## 概述 `MediaQueryList` 是一个用于表示和管理 CSS 媒体查询的 JavaScript 接口。它允许开发者检测媒体查询的适用性变化，并在视口的尺寸或特性发生改变时做出相应的行为。 ## 文档 ### ...
Meta Keywords: mediaquerylist, javascript, matchmedia, window, handlemediachange
-->

# MediaQueryList - JavaScript 媒体查询列表详解

## 概述
`MediaQueryList` 是一个用于表示和管理 CSS 媒体查询的 JavaScript 接口。它允许开发者检测媒体查询的适用性变化，并在视口的尺寸或特性发生改变时做出相应的行为。

## 文档
### 目的
`MediaQueryList` 接口主要用于监听和响应浏览器窗口的尺寸变化，以便根据不同的屏幕条件应用不同的样式或功能。

### 用法
`MediaQueryList` 通过 `window.matchMedia()` 方法创建。该方法接受一个媒体查询字符串，并返回一个 `MediaQueryList` 对象。

#### 语法
```javascript
let mediaQueryList = window.matchMedia(mediaQueryString);
```

- **mediaQueryString**: 一个字符串，表示媒体查询的条件，例如 `"(max-width: 600px)"`。

### 属性
- **matches**: 一个布尔值，指示媒体查询是否匹配当前的文档视口。
- **media**: 返回媒体查询字符串。

### 方法
- **addListener(listener)**: 添加一个监听器，当媒体查询状态发生变化时会调用该监听器。
- **removeListener(listener)**: 移除之前添加的监听器。

## 示例
```javascript
// 创建一个媒体查询列表
let mediaQueryList = window.matchMedia("(max-width: 600px)");

// 定义监听器
function handleMediaChange(event) {
    if (event.matches) {
        console.log("视口宽度小于600px");
    } else {
        console.log("视口宽度大于等于600px");
    }
}

// 添加监听器
mediaQueryList.addListener(handleMediaChange);

// 初始检查
handleMediaChange(mediaQueryList);
```

## 解释
常见的问题包括：
- **兼容性问题**: 某些旧版浏览器可能不支持 `matchMedia()` 方法，因此在使用时需检查浏览器兼容性。
- **性能考虑**: 频繁的媒体查询监听可能会影响性能，因此应当合理使用监听器，并在不需要时及时移除。

## 一句话总结
`MediaQueryList` 是 JavaScript 中用于处理和响应 CSS 媒体查询的强大工具。