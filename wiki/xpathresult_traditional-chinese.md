<!--
Meta Description: # XPathResult：JavaScript 中的 XPath 結果類型 ## 概述 `XPathResult` 是一個 JavaScript 物件，代表 XPath 查詢的結果，通常與 `document.evaluate()` 方法一起使用。它提供了查詢結果的詳細資訊，並支持多種結果類型，以...
Meta Keywords: xpathresult, let, xpath, document, result
-->

# XPathResult：JavaScript 中的 XPath 結果類型

## 概述
`XPathResult` 是一個 JavaScript 物件，代表 XPath 查詢的結果，通常與 `document.evaluate()` 方法一起使用。它提供了查詢結果的詳細資訊，並支持多種結果類型，以便於開發者處理 XML 或 HTML 文檔。

## 文檔
`XPathResult` 類別是用於表示 XPath 查詢的結果集合。當使用 `document.evaluate()` 進行 XPath 查詢時，該方法會返回一個 `XPathResult` 物件，該物件包含了查詢結果的資訊。`XPathResult` 提供了多種屬性和方法，以便開發者能夠輕鬆地獲取和操作查詢結果。

### 主要屬性
- **resultType**: 表示查詢結果的類型，可能的值有 `XPathResult.ANY_TYPE`、`XPathResult.NUMBER_TYPE`、`XPathResult.STRING_TYPE`、`XPathResult.BOOLEAN_TYPE`、`XPathResult.UNORDERED_NODE_ITERATOR_TYPE` 等。
- **stringValue**: 如果查詢結果的類型是字符串，則返回該字符串的值。
- **numberValue**: 如果查詢結果的類型是數字，則返回該數字的值。
- **booleanValue**: 如果查詢結果的類型是布林值，則返回該布林值。
- **singleNodeValue**: 如果查詢結果返回單個節點，則返回該節點。
- **snapshotLength**: 如果查詢結果返回多個節點，則返回結果集中節點的數量。
- **iterateNext()**: 返回結果集中的下一個節點。

### 使用
要使用 `XPathResult`，首先需要調用 `document.evaluate()` 方法來執行 XPath 查詢。該方法的語法如下：

```javascript
let result = document.evaluate(xpathExpression, contextNode, namespaceResolver, resultType, result);
```

### 參數
- **xpathExpression**: 要執行的 XPath 表達式。
- **contextNode**: 執行 XPath 查詢的上下文節點。
- **namespaceResolver**: (可選) 用於解析命名空間的函數。
- **resultType**: (可選) 指定結果類型的常量。
- **result**: (可選) 一個已存在的 `XPathResult` 物件，用於接收結果。

## 範例
以下是如何使用 `XPathResult` 的基本範例：

### 基本範例 1：查詢單個節點
```javascript
let xpathExpression = "//h1";
let contextNode = document;
let result = document.evaluate(xpathExpression, contextNode, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null);
let node = result.singleNodeValue;
console.log(node.textContent); // 輸出 h1 標題的內容
```

### 基本範例 2：查詢多個節點
```javascript
let xpathExpression = "//p";
let contextNode = document;
let result = document.evaluate(xpathExpression, contextNode, null, XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, null);
for (let i = 0; i < result.snapshotLength; i++) {
    let node = result.snapshotItem(i);
    console.log(node.textContent); // 輸出每個 p 標籤的內容
}
```

## 解釋
在使用 `XPathResult` 時，開發者可能會面臨一些常見的陷阱和注意事項：

1. **結果類型**: 確保選擇正確的結果類型，以避免類型錯誤。例如，使用 `XPathResult.FIRST_ORDERED_NODE_TYPE` 來獲取單個節點時，必須使用 `singleNodeValue` 屬性。
2. **命名空間**: 如果查詢涉及命名空間，則需要提供正確的命名空間解析器。
3. **上下文節點**: 確保上下文節點正確，否則查詢可能無法返回預期結果。

## 一句總結
`XPathResult` 是用於表示和處理 XPath 查詢結果的 JavaScript 物件，對於 XML 和 HTML 文檔的操作至關重要。