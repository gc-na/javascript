<!--
Meta Description: # XPathResult 在 JavaScript 中的應用 ## 摘要 XPathResult 是一個與 XPath 查詢結果有關的物件，常用於在 XML 或 HTML 文檔中執行查詢。它提供了對查詢結果的訪問和操作，幫助開發者更有效地處理結構化數據。 ## 文檔 ### 目的 XPathRes...
Meta Keywords: xpathresult, javascript, xpath, let, xml
-->

# XPathResult 在 JavaScript 中的應用

## 摘要
XPathResult 是一個與 XPath 查詢結果有關的物件，常用於在 XML 或 HTML 文檔中執行查詢。它提供了對查詢結果的訪問和操作，幫助開發者更有效地處理結構化數據。

## 文檔
### 目的
XPathResult 主要用於表示 XPath 查詢的結果。當你使用 `document.evaluate()` 方法執行 XPath 查詢時，會返回一個 XPathResult 物件。這個物件允許開發者以多種方式訪問查詢結果，例如單個節點、節點集、數值或布爾值。

### 使用方法
要使用 XPathResult，首先需要使用 `document.evaluate()` 方法來執行 XPath 查詢。這個方法的基本語法如下：

```javascript
let result = document.evaluate(
  xpathExpression,
  contextNode,
  namespaceResolver,
  resultType,
  result
);
```

- **xpathExpression**: 要執行的 XPath 表達式。
- **contextNode**: 查詢的上下文節點，通常是要查詢的 XML 或 HTML 文件的根節點。
- **namespaceResolver**: 可選的命名空間解析器。
- **resultType**: 指定返回結果的類型，XPathResult 物件的類型取決於這個參數。
- **result**: 可選的 XPathResult 物件，用於接收新結果。

### 返回的結果類型
XPathResult 物件的屬性可以用來訪問查詢結果，這些屬性包括：
- `resultType`: 返回結果的類型。
- `booleanValue`: 如果結果類型是布爾值，則返回此值。
- `numberValue`: 如果結果類型是數值，則返回此值。
- `stringValue`: 如果結果類型是字符串，則返回此值。
- `singleNodeValue`: 返回查詢結果的單個節點。
- `snapshotLength`: 如果結果是節點集，則返回節點數量。
- `snapshotItem(index)`: 返回指定索引的節點。

## 範例
以下是使用 XPathResult 的基本範例：

```javascript
// 假設有一個 XML 文件
let xmlString = `<books>
                   <book id="1">JavaScript Basics</book>
                   <book id="2">Advanced JavaScript</book>
                 </books>`;
let parser = new DOMParser();
let xmlDoc = parser.parseFromString(xmlString, "text/xml");

// 使用 XPath 查詢
let xpathExpression = "/books/book[@id='1']";
let result = document.evaluate(xpathExpression, xmlDoc, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null);

// 獲取結果
let bookNode = result.singleNodeValue;
console.log(bookNode.textContent); // 輸出: JavaScript Basics
```

## 解釋
在使用 XPathResult 時，有幾個常見的陷阱需要注意：
1. **結果類型**: 確保正確指定結果類型，否則可能無法正確訪問結果。
2. **命名空間**: 對於 XML 文件，若使用命名空間，需正確提供解析器。
3. **查詢上下文**: 查詢的上下文節點必須正確，否則結果可能不符合預期。

## 一句總結
XPathResult 是 JavaScript 中用於表示和操作 XPath 查詢結果的物件，幫助開發者高效處理結構化數據。