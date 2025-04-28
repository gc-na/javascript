<!--
Meta Description: # CSSRuleList：JavaScript 中的 CSS 規則列表 ## 簡介 CSSRuleList 是一個用於表示 CSS 規則集合的物件，通常用於操作和查詢 CSS 樣式表中的規則。它在 JavaScript 中非常重要，特別是在動態修改樣式或檢查樣式表內容的情況下。 ## 文件說明 C...
Meta Keywords: cssrulelist, css, const, cssrules, stylesheets
-->

# CSSRuleList：JavaScript 中的 CSS 規則列表

## 簡介
CSSRuleList 是一個用於表示 CSS 規則集合的物件，通常用於操作和查詢 CSS 樣式表中的規則。它在 JavaScript 中非常重要，特別是在動態修改樣式或檢查樣式表內容的情況下。

## 文件說明
CSSRuleList 物件是由 CSSStyleSheet 的 cssRules 屬性返回的，表示一組 CSS 規則。每個 CSSRuleList 包含多個 CSSRule 物件，這些物件代表不同的 CSS 規則，如選擇器、樣式、媒體查詢等。

### 目的
CSSRuleList 使開發者能夠以編程的方式訪問和修改 CSS 樣式，從而提高網頁的互動性和動態效果。

### 用法
在 JavaScript 中，我們可以通過訪問樣式表的 cssRules 屬性獲得 CSSRuleList。以下是基本用法：

```javascript
const styleSheets = document.styleSheets; // 獲取所有樣式表
const firstStyleSheet = styleSheets[0]; // 獲取第一個樣式表
const rules = firstStyleSheet.cssRules; // 獲取 CSS 規則列表
```

### 詳細說明
- **屬性**：CSSRuleList 物件本身包含一系列 CSSRule 物件，這些物件可以通過索引來訪問。
- **方法**：CSSRuleList 不具備方法，但可以使用標準的 Array 方法，如 `forEach`, `map`, `filter` 等進行操作。
- **可變性**：CSSRuleList 是動態的，當樣式表中的規則改變時，CSSRuleList 也會相應更新。

## 範例
以下是一些基本用法示例：

### 獲取所有樣式規則
```javascript
const styleSheets = document.styleSheets;
const firstStyleSheet = styleSheets[0];
const rules = firstStyleSheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    console.log(rules[i].cssText); // 輸出每個 CSS 規則
}
```

### 修改特定規則
```javascript
const firstStyleSheet = document.styleSheets[0];
const firstRule = firstStyleSheet.cssRules[0]; // 獲取第一條規則
firstRule.style.backgroundColor = 'red'; // 修改背景顏色
```

## 解釋
在使用 CSSRuleList 時，有幾個常見的陷阱與注意事項：
- **跨域問題**：如果樣式表來自不同的域，則無法訪問其 cssRules，這會引發安全性錯誤。
- **動態更新**：當樣式表中的規則發生變化時，必須重新獲取 cssRules，以確保操作的是最新的規則。
- **瀏覽器支持**：雖然大多數現代瀏覽器都支持 CSSRuleList，但舊版瀏覽器的支持情況可能有所不同。

## 一句話總結
CSSRuleList 是一個用於表示和操作 CSS 樣式表中規則的物件，對於動態修改網頁樣式至關重要。