<!--
Meta Description: # JavaScript 剪贴板 API 使用指南 ## 概述 JavaScript 剪贴板 API 允许开发者访问和操作用户的剪贴板内容，支持文本的复制和粘贴功能。它为 Web 应用提供了与用户剪贴板交互的能力。 ## 文档 ### 目的 剪贴板 API 旨在简化在 Web 应用中处理剪贴板内容的...
Meta Keywords: api, javascript, 剪贴板, navigator, clipboard
-->

# JavaScript 剪贴板 API 使用指南

## 概述
JavaScript 剪贴板 API 允许开发者访问和操作用户的剪贴板内容，支持文本的复制和粘贴功能。它为 Web 应用提供了与用户剪贴板交互的能力。

## 文档
### 目的
剪贴板 API 旨在简化在 Web 应用中处理剪贴板内容的过程，使得用户可以方便地复制和粘贴文本。

### 使用方法
剪贴板 API 主要通过 `navigator.clipboard` 对象提供。常用的方法包括 `writeText()` 和 `readText()`。

- **`navigator.clipboard.writeText(text)`**
  - **参数**: `text` (字符串) - 要复制到剪贴板的文本。
  - **返回**: 返回一个 Promise，表示操作的成功与否。

- **`navigator.clipboard.readText()`**
  - **返回**: 返回一个 Promise，解析为剪贴板中的文本。

### 详细信息
- 必须在 HTTPS 环境下使用剪贴板 API，或者在 localhost 中进行测试。
- 用户必须与页面进行交互（如点击事件）才能使用剪贴板 API，以确保安全性。

## 示例
### 复制文本到剪贴板
```javascript
function copyToClipboard() {
    const textToCopy = "Hello, World!";
    navigator.clipboard.writeText(textToCopy)
        .then(() => {
            console.log("文本已复制到剪贴板!");
        })
        .catch(err => {
            console.error("复制失败: ", err);
        });
}
```

### 从剪贴板读取文本
```javascript
function readFromClipboard() {
    navigator.clipboard.readText()
        .then(text => {
            console.log("剪贴板内容: ", text);
        })
        .catch(err => {
            console.error("读取失败: ", err);
        });
}
```

## 解释
- **常见问题**: 
  - 由于安全限制，调用剪贴板 API 的操作必须在用户交互后执行，如点击按钮，而不能在页面加载时自动执行。
  - 不支持旧版浏览器，确保使用的浏览器版本支持剪贴板 API。

- **注意事项**: 
  - 在某些浏览器中，用户需要允许页面访问剪贴板。
  - 处理 Promise 时要注意异常，确保提供用户友好的错误信息。

## 一句话总结
JavaScript 剪贴板 API 提供了简洁的方法来操作用户剪贴板，实现文本的复制和粘贴功能。