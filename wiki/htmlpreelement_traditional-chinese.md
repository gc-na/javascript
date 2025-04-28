<!--
Meta Description: # HTMLPreElement：JavaScript 中的 HTML `<pre>` 元素 ## 概述 `HTMLPreElement` 是一個 JavaScript 接口，代表 HTML 文檔中的 `<pre>` 元素。這個元素用於表示預格式化的文本，通常用於顯示保留空白和換行的內容。 ## 文...
Meta Keywords: pre, htmlpreelement, javascript, document, html
-->

# HTMLPreElement：JavaScript 中的 HTML `<pre>` 元素

## 概述
`HTMLPreElement` 是一個 JavaScript 接口，代表 HTML 文檔中的 `<pre>` 元素。這個元素用於表示預格式化的文本，通常用於顯示保留空白和換行的內容。

## 文件說明
`HTMLPreElement` 介面提供了對 `<pre>` 元素的操作和屬性訪問功能。這個元素的主要功能是顯示以固定寬度字體排版的文本，並保留文本中的空格和換行，適合用於顯示代碼或其他格式化文本。

### 目的
`HTMLPreElement` 的主要目的在於顯示預格式化的內容，讓開發者能夠以更具可讀性的方式展示代碼、文章或其他需要精確排版的文本。

### 使用方法
當您使用 JavaScript 操作 DOM 時，可以通過 `document.createElement('pre')` 創建一個新的 `<pre>` 元素，或者通過 `document.getElementsByTagName('pre')` 獲取現有的 `<pre>` 元素。

### 屬性
- `textContent`：設置或獲取 `<pre>` 元素的文本內容。
- `innerHTML`：設置或獲取 `<pre>` 元素的 HTML 內容。

## 範例
### 創建和操作 `<pre>` 元素的基本範例
```javascript
// 創建一個新的 <pre> 元素
const preElement = document.createElement('pre');
preElement.textContent = `function helloWorld() {
    console.log("Hello, World!");
}`;

// 將 <pre> 元素添加到文檔中
document.body.appendChild(preElement);
```

### 獲取和修改現有的 `<pre>` 元素
```javascript
// 獲取第一個 <pre> 元素
const existingPreElement = document.getElementsByTagName('pre')[0];

// 修改其內容
existingPreElement.textContent = '這是修改後的文本。';
```

## 說明
使用 `HTMLPreElement` 時，有幾個常見的陷阱需要注意：
- 確保使用 `textContent` 而非 `innerHTML` 來避免 XSS 攻擊，因為 `innerHTML` 會解析 HTML 結構，可能導致安全風險。
- 當在 `<pre>` 元素中使用 CSS 樣式時，請注意樣式如何影響預格式化文本的顯示效果。

## 一句總結
`HTMLPreElement` 讓開發者能夠在 JavaScript 中輕鬆操作和顯示預格式化的文本內容。