<!--
Meta Description: # StyleSheetList：JavaScript中的樣式表清單物件 ## 概述 `StyleSheetList` 是一個在 JavaScript 中用來表示樣式表的集合的介面，主要用於操作和訪問文檔中的所有樣式表。它是 `document.styleSheets` 屬性所返回的物件，讓開發者能...
Meta Keywords: stylesheetlist, stylesheets, javascript, document, length
-->

# StyleSheetList：JavaScript中的樣式表清單物件

## 概述
`StyleSheetList` 是一個在 JavaScript 中用來表示樣式表的集合的介面，主要用於操作和訪問文檔中的所有樣式表。它是 `document.styleSheets` 屬性所返回的物件，讓開發者能夠輕鬆地獲取和修改樣式。

## 文檔
`StyleSheetList` 是一個類似於陣列的物件，提供了一個包含當前文檔所有樣式表的清單。每個樣式表可以是外部樣式表或內嵌樣式表。此介面允許開發者透過索引來訪問樣式表並進行操作。

### 目的
`StyleSheetList` 的主要目的是提供一個方便的方式來操作和檢索文檔中的所有樣式表，這對於動態更新樣式或進行樣式的條件性應用非常有用。

### 使用方法
要使用 `StyleSheetList`，只需訪問 `document.styleSheets` 屬性，這將返回一個 `StyleSheetList` 物件。你可以使用索引來訪問特定的樣式表，並且該物件提供了一些方法來操作樣式規則。

### 屬性
- `length`: 返回樣式表的數量。
- `item(index)`: 根據索引返回指定的樣式表。

## 示例
以下是一些基本的使用範例：

### 例子 1：訪問樣式表
```javascript
const styleSheets = document.styleSheets;
console.log(`樣式表的數量: ${styleSheets.length}`);

for (let i = 0; i < styleSheets.length; i++) {
    console.log(`樣式表 ${i}: ${styleSheets[i].href}`);
}
```

### 例子 2：使用 item 方法
```javascript
const firstStyleSheet = document.styleSheets.item(0);
console.log(`第一個樣式表的連結: ${firstStyleSheet.href}`);
```

### 例子 3：查看樣式表的規則
```javascript
const styleSheet = document.styleSheets[0];
const rules = styleSheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    console.log(`第 ${i} 條規則: ${rules[i].cssText}`);
}
```

## 解釋
使用 `StyleSheetList` 時，有幾個常見的注意事項：

- **跨域問題**：如果樣式表是跨域的，則無法訪問其內容，這會引發安全錯誤。
- **動態樣式表**：如果在 JavaScript 中動態添加或移除樣式表，`StyleSheetList` 會自動更新。
- **CSS 規則的支持**：並非所有的 CSS 規則都可以被 JavaScript 操作，某些規則可能是只讀的。

## 一句話總結
`StyleSheetList` 是一個用於獲取和操作文檔中所有樣式表的 JavaScript 介面。