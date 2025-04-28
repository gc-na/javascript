<!--
Meta Description: # DOMImplementation：JavaScript 中的文檔物件模型實現 ## 簡介 DOMImplementation 是一個介面，提供了一組方法來創建和操作文檔物件模型（DOM）的實例。它使開發者可以建立新的文檔、元素和標記，並支持 HTML 和 XML 的操作。 ## 文檔 ### ...
Meta Keywords: html, domimplementation, javascript, dom, xml
-->

# DOMImplementation：JavaScript 中的文檔物件模型實現

## 簡介
DOMImplementation 是一個介面，提供了一組方法來創建和操作文檔物件模型（DOM）的實例。它使開發者可以建立新的文檔、元素和標記，並支持 HTML 和 XML 的操作。

## 文檔
### 目的
DOMImplementation 介面主要用於創建和操作 DOM 文檔。它的主要功能包括創建新的文檔、獲取支持的特性及其版本，並提供對於文檔的操作方法。

### 用法
DOMImplementation 通常在 JavaScript 中通過 `document.implementation` 屬性訪問。這個屬性返回一個 DOMImplementation 物件，開發者可以使用該物件來創建新的文檔或元素。

#### 方法
1. **createDocument(namespaceURI, qualifiedName, doctype)**: 創建一個新的 XML 文檔。
2. **createHTMLDocument(title)**: 創建一個新的 HTML 文檔。
3. **hasFeature(feature, version)**: 檢查是否支持特定的功能和版本。

### 詳細資訊
- `createDocument` 方法返回一個新的文檔對象，參數 `namespaceURI` 指定文檔的命名空間，`qualifiedName` 是文檔的根元素名稱，`doctype` 是可選的文檔類型聲明。
- `createHTMLDocument` 方法返回一個新的 HTML 文檔，並可以指定文檔的標題。
- `hasFeature` 方法允許開發者檢查當前環境是否支持某個特定的 DOM 特性，這對於編寫跨瀏覽器的代碼非常重要。

## 範例
### 創建 XML 文檔
```javascript
const xmlDoc = document.implementation.createDocument("http://www.w3.org/1999/xhtml", "html", null);
console.log(xmlDoc.documentElement.nodeName); // "html"
```

### 創建 HTML 文檔
```javascript
const htmlDoc = document.implementation.createHTMLDocument("新文檔");
console.log(htmlDoc.title); // "新文檔"
```

### 檢查功能支持
```javascript
const isSupported = document.implementation.hasFeature("HTML", "1.0");
console.log(isSupported); // true 或 false
```

## 解釋
使用 DOMImplementation 時，開發者應注意以下幾點：
- 確保所使用的命名空間正確，尤其是在創建 XML 文檔時。
- 不同的瀏覽器可能支持不同的 DOM 特性，因此在檢查功能支持時，最好先獲取用戶的瀏覽器信息。
- 對於 HTML 文檔，創建時可使用 `createHTMLDocument` 方法，這將自動設置文檔的基本結構。

## 一句總結
DOMImplementation 是 JavaScript 中用於創建和操作文檔物件模型的強大介面。