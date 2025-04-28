<!--
Meta Description: # CSSRule：JavaScript 中的 CSS 規則對象 ## 簡介 `CSSRule` 是一個表示 CSS 規則的 JavaScript 對象。在 Web 開發中，通過 JavaScript 操作 CSS 規則可以為動態樣式的應用提供強大的支持。 ## 文件說明 `CSSRule` 對象是...
Meta Keywords: cssrule, css, javascript, stylesheet, document
-->

# CSSRule：JavaScript 中的 CSS 規則對象

## 簡介
`CSSRule` 是一個表示 CSS 規則的 JavaScript 對象。在 Web 開發中，通過 JavaScript 操作 CSS 規則可以為動態樣式的應用提供強大的支持。

## 文件說明
`CSSRule` 對象是 Document Object Model (DOM) 的一部分，允許開發者以程式化的方式訪問和修改樣式表中的 CSS 規則。這對於動態應用樣式或在運行時修改樣式非常有用。`CSSRule` 提供了一系列屬性和方法，使得開發者可以精確控制元素的樣式。

### 目的
`CSSRule` 的主要目的是讓開發者能夠在 JavaScript 中以物件的方式操作 CSS 規則，這樣可以輕鬆地更改樣式、添加新規則或刪除不必要的規則。

### 使用方式
`CSSRule` 主要通過樣式表 (StyleSheet) 對象來訪問。開發者可以通過 `document.styleSheets` 獲取所有樣式表，然後進一步獲取 `CSSRule` 對象。

### 屬性
- `type`: 返回 CSS 規則的類型（例如，樣式規則、媒體規則等）。
- `selectorText`: 獲取或設置該規則的選擇器文本。
- `style`: 獲取該規則的樣式屬性。

## 範例
以下是一些使用 `CSSRule` 的基本範例：

### 獲取樣式規則
```javascript
const styleSheet = document.styleSheets[0]; // 獲取第一個樣式表
const cssRules = styleSheet.cssRules; // 獲取所有 CSS 規則
console.log(cssRules[0].selectorText); // 輸出第一條規則的選擇器
```

### 修改樣式規則
```javascript
const styleSheet = document.styleSheets[0]; // 獲取第一個樣式表
const cssRule = styleSheet.cssRules[0]; // 獲取第一條 CSS 規則
cssRule.style.color = "red"; // 將該規則的文字顏色設置為紅色
```

### 添加新的 CSS 規則
```javascript
const styleSheet = document.styleSheets[0]; // 獲取第一個樣式表
styleSheet.insertRule("body { background-color: blue; }", styleSheet.cssRules.length); // 在樣式表結尾處添加新規則
```

## 解釋
在使用 `CSSRule` 時，開發者應注意以下幾點：
- 不同類型的 CSS 規則有不同的屬性。例如，`@media` 規則不會有 `selectorText` 屬性。
- 修改 `CSSRule` 會影響到當前的樣式，這可能會導致樣式的意外改變，因此在修改之前應先確保了解當前的樣式結構。
- 某些瀏覽器可能對 `CSSRule` 的實現有所不同，因此在使用前最好進行測試。

## 一句總結
`CSSRule` 是 JavaScript 中一個強大的對象，允許開發者以程式化的方式操作和修改 CSS 規則。