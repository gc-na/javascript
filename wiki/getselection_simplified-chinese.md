<!--
Meta Description: # JavaScript 中的 getSelection 方法详解 ## 概述 `getSelection` 是一个用于获取用户在网页中选定文本的 JavaScript 方法。它属于 `Window` 接口，允许开发者访问和操作用户的文本选择。 ## 文档 ### 目的 `getSelection`...
Meta Keywords: getselection, selection, javascript, const, window
-->

# JavaScript 中的 getSelection 方法详解

## 概述
`getSelection` 是一个用于获取用户在网页中选定文本的 JavaScript 方法。它属于 `Window` 接口，允许开发者访问和操作用户的文本选择。

## 文档
### 目的
`getSelection` 方法的主要目的是获取用户在文档中选定的文本。它返回一个 `Selection` 对象，表示用户当前的文本选择，开发者可以利用该对象进行进一步的操作，例如高亮、复制或删除选定文本。

### 用法
`getSelection` 方法的语法非常简单：
```javascript
const selection = window.getSelection();
```

### 返回值
- 返回一个 `Selection` 对象，包含用户选中的文本及其相关信息。

### 详细信息
- `Selection` 对象包含多种方法和属性，可以用来获取或操作选定的文本。
- 通过 `toString()` 方法可以获取选中的文本内容：
  ```javascript
  const selectedText = selection.toString();
  ```
- 还可以通过 `rangeCount` 属性获取选中的范围数量，利用 `getRangeAt()` 方法访问具体的选区范围。

## 示例
### 基本用法
```javascript
// 获取用户选定的文本
const selection = window.getSelection();
const selectedText = selection.toString();
console.log(`用户选定的文本是: "${selectedText}"`);
```

### 高亮选定文本
```javascript
// 高亮选定的文本
const selection = window.getSelection();
if (selection.rangeCount > 0) {
    const range = selection.getRangeAt(0);
    const span = document.createElement('span');
    span.style.backgroundColor = 'yellow';
    range.surroundContents(span);
}
```

## 说明
- **常见错误**：在没有用户选定任何文本的情况下调用 `getSelection` 可能返回一个空的 `Selection` 对象，因此在使用之前应检查 `rangeCount`。
- **跨文档选择**：`getSelection` 只能在同一文档中有效，不能跨越不同的文档或 iframe。
- **权限限制**：某些浏览器可能限制对 `getSelection` 的使用，尤其是在没有用户交互的情况下。

## 一句话总结
`getSelection` 方法是 JavaScript 中用于获取和操作用户选定文本的强大工具。