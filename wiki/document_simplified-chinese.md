<!--
Meta Description: # JavaScript 中的 document 对象：全面指南 ## 概述 在 JavaScript 中，`document` 对象是浏览器提供的一个接口，用于访问和操作网页的内容。它是 DOM（文档对象模型）的根节点，允许开发者以编程方式修改 HTML 文档的结构、样式和内容。 ## 文档 ##...
Meta Keywords: document, javascript, 获取元素, getelementbyid, queryselector
-->

# JavaScript 中的 document 对象：全面指南

## 概述
在 JavaScript 中，`document` 对象是浏览器提供的一个接口，用于访问和操作网页的内容。它是 DOM（文档对象模型）的根节点，允许开发者以编程方式修改 HTML 文档的结构、样式和内容。

## 文档

### 目的
`document` 对象使开发者能够与网页进行互动，获取元素、添加或删除内容、修改样式等。它是实现动态网页的重要组成部分。

### 用法
`document` 对象可以通过 JavaScript 代码直接访问，通常在 `<script>` 标签中使用。以下是一些常见的用法：

- 获取元素：`document.getElementById()`, `document.querySelector()`
- 创建元素：`document.createElement()`
- 修改内容：`element.innerHTML`, `element.textContent`
- 添加事件监听器：`element.addEventListener()`

### 详细信息
- **获取元素**：`document.getElementById('id')` 返回具有指定 ID 的元素，`document.querySelector('.class')` 返回第一个匹配的元素。
- **创建元素**：使用 `document.createElement('tagName')` 创建一个新的元素节点。
- **修改网页**：可以通过属性如 `innerHTML` 和 `textContent` 来更新元素的内容。
- **事件处理**：通过 `addEventListener` 方法，可以为元素添加事件处理程序。

## 示例

### 获取元素
```javascript
var header = document.getElementById('header');
console.log(header);
```

### 创建新元素
```javascript
var newDiv = document.createElement('div');
newDiv.innerHTML = '这是一个新创建的 div';
document.body.appendChild(newDiv);
```

### 修改内容
```javascript
var paragraph = document.querySelector('p');
paragraph.textContent = '这段文本已被修改。';
```

### 添加事件监听器
```javascript
var button = document.getElementById('myButton');
button.addEventListener('click', function() {
    alert('按钮被点击了！');
});
```

## 解释
在使用 `document` 对象时，开发者常常会遇到以下问题：

- **元素未加载**：在 DOM 完全加载之前执行脚本可能导致无法找到元素。解决方法是将脚本放在文档底部，或使用 `DOMContentLoaded` 事件。
- **选择器问题**：使用 `querySelector` 和 `querySelectorAll` 时，确认选择器的正确性以确保返回预期的元素。
- **跨域问题**：对跨域 iframe 的 `document` 访问会受到限制，确保在同源策略下操作。

## 一句话总结
`document` 对象是 JavaScript 中用于访问和操作网页内容的核心接口。