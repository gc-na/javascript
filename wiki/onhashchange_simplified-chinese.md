<!--
Meta Description: # JavaScript中的onhashchange事件详解 ## 概述 `onhashchange`是一个JavaScript事件，用于监听浏览器地址栏中的哈希（#）部分的变化。当用户通过链接、JavaScript代码或浏览器的后退/前进按钮修改URL的哈希值时，会触发此事件。 ## 文档 `on...
Meta Keywords: onhashchange, location, hash, window, addeventlistener
-->

# JavaScript中的onhashchange事件详解

## 概述
`onhashchange`是一个JavaScript事件，用于监听浏览器地址栏中的哈希（#）部分的变化。当用户通过链接、JavaScript代码或浏览器的后退/前进按钮修改URL的哈希值时，会触发此事件。

## 文档
`onhashchange`事件是`window`对象的一个属性，通常与`addEventListener`方法结合使用。它在哈希值发生变化时触发，允许开发者处理与哈希相关的状态变化。使用该事件可以实现单页面应用程序（SPA）中的路由导航。

### 使用方法
```javascript
window.onhashchange = function() {
    // 处理哈希变化的代码
};
```
或使用`addEventListener`：
```javascript
window.addEventListener('hashchange', function() {
    // 处理哈希变化的代码
});
```

### 事件对象
当`onhashchange`事件触发时，会提供一个事件对象，包含以下属性：
- `oldURL`: 事件触发前的完整URL。
- `newURL`: 事件触发后的完整URL。

## 示例
### 基本用法
```javascript
window.onhashchange = function() {
    console.log('哈希发生变化！新哈希值为：' + location.hash);
};

// 模拟哈希变化
location.hash = '#section1'; // 控制台输出：哈希发生变化！新哈希值为：#section1
location.hash = '#section2'; // 控制台输出：哈希发生变化！新哈希值为：#section2
```

### 使用addEventListener
```javascript
function handleHashChange() {
    console.log('当前哈希值为：' + location.hash);
}

window.addEventListener('hashchange', handleHashChange);

// 修改哈希值
location.hash = '#home';   // 控制台输出：当前哈希值为：#home
location.hash = '#about';  // 控制台输出：当前哈希值为：#about
```

## 说明
- **兼容性**：`onhashchange`事件在大多数现代浏览器中均得到支持。但在使用时需注意旧版IE浏览器（例如IE8及以下）不支持此事件。
- **性能**：频繁触发此事件可能会影响性能，因此建议在事件处理函数中合理使用节流技术。
- **历史记录**：此事件与`history.pushState()`和`history.replaceState()`结合使用时需谨慎，因为它们不会触发`onhashchange`事件。
- **初始加载**：在页面加载时，若地址中已包含哈希值，`onhashchange`事件不会被触发。可以在页面加载时手动调用处理函数以处理初始状态。

## 一句话总结
`onhashchange`事件在JavaScript中用于监听和响应浏览器地址栏哈希值的变化，便于实现动态路由和状态管理。