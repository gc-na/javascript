<!--
Meta Description: # DOMParser：JavaScript 中解析 HTML 和 XML 的利器 ## 概述 DOMParser 是一個用於將字符串形式的 HTML 或 XML 內容轉換為 Document 物件的 JavaScript API。這使得開發者能夠輕鬆地操作和查詢這些文檔。 ## 文檔 ### 目的...
Meta Keywords: html, xml, domparser, const, parsefromstring
-->

# DOMParser：JavaScript 中解析 HTML 和 XML 的利器

## 概述
DOMParser 是一個用於將字符串形式的 HTML 或 XML 內容轉換為 Document 物件的 JavaScript API。這使得開發者能夠輕鬆地操作和查詢這些文檔。

## 文檔
### 目的
DOMParser 的主要目的是允許開發者從字符串中生成 DOM 文檔，這樣可以方便地操作和提取數據。它特別適用於從外部數據源獲取 HTML 或 XML 字符串時。

### 使用方法
DOMParser 的基本用法如下：

1. 創建一個 DOMParser 的實例。
2. 使用 `parseFromString` 方法，將字符串轉換為 DOM 文檔。

### 詳細說明
```javascript
const parser = new DOMParser();
const doc = parser.parseFromString(string, mimeType);
```
- `string`：要解析的 HTML 或 XML 字符串。
- `mimeType`：指定內容類型，可以是 `"text/html"` 或 `"application/xml"`。

如果字符串無法正確解析，將返回一個包含錯誤信息的 Document 物件。

## 範例
### 基本用法
```javascript
// 解析 HTML 字符串
const htmlString = '<div><h1>Hello, World!</h1></div>';
const parser = new DOMParser();
const doc = parser.parseFromString(htmlString, 'text/html');
console.log(doc.body.innerHTML); // <div><h1>Hello, World!</h1></div>

// 解析 XML 字符串
const xmlString = '<note><to>Tove</to><from>Jani</from><heading>Reminder</heading><body>Don\'t forget me this weekend!</body></note>';
const xmlDoc = parser.parseFromString(xmlString, 'application/xml');
console.log(xmlDoc.getElementsByTagName('to')[0].textContent); // Tove
```

## 解釋
- **常見陷阱**：解析 HTML 字符串時，若字符串包含無效的 HTML，可能會導致解析錯誤。使用 XML 時，需確保格式正確，否則將會返回一個錯誤文檔。
- **錯誤處理**：當使用 `parseFromString` 解析 XML 時，若出現錯誤，可以檢查返回的 Document 物件，使用 `getElementsByTagName('parsererror')` 獲取具體錯誤信息。
- **性能考慮**：不建議在高性能要求的環境中頻繁使用 DOMParser，因為解析可能會消耗較多的計算資源。

## 總結
DOMParser 是一個強大的工具，能夠將字符串形式的 HTML 和 XML 轉換為可操作的 DOM 文檔，方便開發者進行數據處理和操作。