<!--
Meta Description: # HTMLPreElement 在 JavaScript 中的使用 ## 概述 HTMLPreElement 是 JavaScript 中用于操作 `<pre>` 元素的接口。该接口允许开发者在网页中处理预格式化文本，保持文本的原始格式和空白字符。 ## 文档 ### 目的 HTMLPreElem...
Meta Keywords: pre, document, htmlpreelement, javascript, newpreelement
-->

# HTMLPreElement 在 JavaScript 中的使用

## 概述
HTMLPreElement 是 JavaScript 中用于操作 `<pre>` 元素的接口。该接口允许开发者在网页中处理预格式化文本，保持文本的原始格式和空白字符。

## 文档
### 目的
HTMLPreElement 主要用于表示预格式化文本，它在 HTML 中通过 `<pre>` 标签实现。该元素的文本内容会以固定宽度字体显示，并保留空格和换行符。在 JavaScript 中，HTMLPreElement 提供了对该元素的访问和操作能力，方便开发者动态修改内容和样式。

### 用法
在 JavaScript 中，开发者可以通过多种方式创建和访问 HTMLPreElement：

1. **访问现有元素**：
   使用 `document.getElementsByTagName` 或 `document.querySelector` 等方法获取 `<pre>` 元素。
   
   ```javascript
   const preElement = document.querySelector('pre');
   ```

2. **创建新元素**：
   使用 `document.createElement` 方法创建新的 `<pre>` 元素并将其添加到页面中。

   ```javascript
   const newPreElement = document.createElement('pre');
   newPreElement.textContent = '这是预格式化文本。';
   document.body.appendChild(newPreElement);
   ```

### 详细信息
- **属性和方法**：
  - `textContent`：用于设置或获取 `<pre>` 元素中的文本内容。
  - `innerHTML`：可以用来设置或获取 `<pre>` 元素的 HTML 内容，但需谨慎使用以避免 XSS 攻击。
  
- **样式**：
  `<pre>` 元素的默认样式通常使用等宽字体。开发者可以通过 CSS 修改其外观，设置字体、颜色、边距等。

## 示例
### 示例 1：访问和修改现有的 `<pre>` 元素
```html
<pre id="myPre">原始文本</pre>
<script>
   const preElement = document.getElementById('myPre');
   preElement.textContent = '修改后的文本\n带有换行符。';
</script>
```

### 示例 2：创建新 `<pre>` 元素
```html
<script>
   const newPreElement = document.createElement('pre');
   newPreElement.textContent = '这是新添加的预格式化文本。';
   document.body.appendChild(newPreElement);
</script>
```

## 说明
在使用 HTMLPreElement 时，开发者应该注意以下几点：
- **避免使用 innerHTML**：如果需要插入用户生成的内容，使用 `textContent` 更为安全，以防止代码注入。
- **样式影响**：由于 `<pre>` 元素的默认样式与其他元素不同，确保在设计布局时考虑其特性。

## 一句话总结
HTMLPreElement 是 JavaScript 中用于操作和管理 `<pre>` 元素的接口，便于处理预格式化文本及其样式。