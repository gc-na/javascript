<!--
Meta Description: # DOMParser：JavaScript 中用於解析 XML 和 HTML 的強大工具 ## 簡介 `DOMParser` 是一個 JavaScript 內建對象，允許開發者將字符串格式的 XML 或 HTML 轉換為可操作的文檔對象模型（DOM）節點。這使得開發者能夠以程式化的方式處理和操作這...
Meta Keywords: xml, html, domparser, javascript, const
-->

# DOMParser：JavaScript 中用於解析 XML 和 HTML 的強大工具

## 簡介
`DOMParser` 是一個 JavaScript 內建對象，允許開發者將字符串格式的 XML 或 HTML 轉換為可操作的文檔對象模型（DOM）節點。這使得開發者能夠以程式化的方式處理和操作這些文檔。

## 文檔
`DOMParser` 的主要目的在於將文本格式的 XML 或 HTML 解析為 DOM 樹，這樣開發者可以使用 JavaScript 來訪問和操作各種元素。此對象的一個重要方法是 `parseFromString`，它接受兩個參數：要解析的字符串和內容類型（如 "text/html" 或 "text/xml"）。

### 使用方式
以下是 `DOMParser` 的基本用法：

```javascript
// 創建一個 DOMParser 實例
const parser = new DOMParser();

// 解析 HTML 字符串
const doc = parser.parseFromString('<div>Hello World</div>', 'text/html');

// 解析 XML 字符串
const xmlDoc = parser.parseFromString('<note><to>Tove</to><from>Jani</from></note>', 'text/xml');
```

### 參數
- `string`：要解析的字符串，可以是 HTML 或 XML 格式。
- `contentType`：指定解析的內容類型，常見的有：
  - `"text/html"`：用於解析 HTML 文檔。
  - `"text/xml"`：用於解析 XML 文檔。

### 返回值
`parseFromString` 方法返回一個 `Document` 對象，這是一個可以進一步操作的 DOM 物件。

## 範例
以下是幾個基本的使用範例：

### 解析 HTML
```javascript
const htmlString = '<ul><li>Item 1</li><li>Item 2</li></ul>';
const parser = new DOMParser();
const doc = parser.parseFromString(htmlString, 'text/html');
console.log(doc.body.firstChild); // 輸出 <ul>...</ul>
```

### 解析 XML
```javascript
const xmlString = '<book><title>JavaScript Guide</title><author>Jane Doe</author></book>';
const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlString, 'text/xml');
console.log(xmlDoc.getElementsByTagName('title')[0].textContent); // 輸出 JavaScript Guide
```

## 解釋
在使用 `DOMParser` 時，開發者需要注意幾個常見的陷阱：

1. **錯誤的內容類型**：如果使用不正確的內容類型解析字符串，可能會導致解析失敗或返回不正確的結果。
2. **XML 命名空間**：在處理 XML 時，命名空間的問題可能會導致查找元素失敗，需謹慎處理。
3. **安全性問題**：直接解析來自不受信任來源的字符串可能會引入安全風險。建議在解析之前對輸入進行驗證和清理。

## 一句總結
`DOMParser` 是一個強大的 JavaScript 工具，用於將字符串格式的 XML 和 HTML 解析為可操作的 DOM 結構。