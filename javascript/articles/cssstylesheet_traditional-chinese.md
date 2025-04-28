<!--
Meta Description: # CSSStyleSheet：JavaScript 操作 CSS 樣式表的強大工具 ## 概述 `CSSStyleSheet` 是一個 JavaScript 介面，允許開發者以程式化的方式訪問和操作 CSS 樣式表。這使得動態修改網頁樣式變得更加靈活和強大。 ## 文檔 ### 目的 `CSSSt...
Meta Keywords: css, cssstylesheet, insertrule, stylesheet, javascript
-->

# CSSStyleSheet：JavaScript 操作 CSS 樣式表的強大工具

## 概述
`CSSStyleSheet` 是一個 JavaScript 介面，允許開發者以程式化的方式訪問和操作 CSS 樣式表。這使得動態修改網頁樣式變得更加靈活和強大。

## 文檔
### 目的
`CSSStyleSheet` 介面代表一個 CSS 樣式表，並提供了多種方法和屬性來操作 CSS 規則。這對於需要在客戶端動態修改樣式的應用特別有用。

### 使用方式
要使用 `CSSStyleSheet`，通常需要通過 `document.styleSheets` 獲取樣式表的陣列，然後可以通過指定的索引來訪問特定的樣式表。

### 詳細信息
- **屬性**
  - `cssRules`: 返回樣式表中的所有 CSS 規則的集合。
  - `insertRule()`: 在樣式表的指定位置插入一條新的 CSS 規則。
  - `deleteRule()`: 刪除指定位置的 CSS 規則。

- **方法**
  - `insertRule(rule: string, index?: number)`: 插入新的 CSS 規則。可選的 `index` 參數指定插入位置，默認為樣式表末尾。
  - `deleteRule(index: number)`: 刪除指定索引的規則。

## 範例
### 基本用法範例
以下是如何使用 `CSSStyleSheet` 來插入和刪除 CSS 規則的範例：

```javascript
// 獲取第一個樣式表
const styleSheet = document.styleSheets[0];

// 插入新的 CSS 規則
styleSheet.insertRule('body { background-color: lightblue; }', styleSheet.cssRules.length);

// 刪除第一條規則
styleSheet.deleteRule(0);
```

## 解釋
在使用 `CSSStyleSheet` 時，開發者需要注意以下幾點：
- 確保樣式表已經加載，否則 `document.styleSheets` 可能不會返回預期的樣式表。
- 在某些瀏覽器中，對於 `insertRule` 的支持可能會有所不同，開發者應檢查相容性。
- 當刪除規則時，應注意索引的變化，因為刪除操作會影響後續規則的索引。

## 一句話總結
`CSSStyleSheet` 介面提供了一種靈活的方式來以程式化方式操作 CSS 樣式表，使得網頁樣式的動態修改更加簡單。