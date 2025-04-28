<!--
Meta Description: # CSSPropertyRule：JavaScript 中的 CSS 屬性規則 ## Synopsis CSSPropertyRule 是一個 JavaScript 物件，允許開發者以編程方式訪問和修改 CSS 樣式規則，主要用於動態改變網頁的樣式。 ## Documentation CSSPro...
Meta Keywords: csspropertyrule, css, rule, javascript, let
-->

# CSSPropertyRule：JavaScript 中的 CSS 屬性規則

## Synopsis
CSSPropertyRule 是一個 JavaScript 物件，允許開發者以編程方式訪問和修改 CSS 樣式規則，主要用於動態改變網頁的樣式。

## Documentation
CSSPropertyRule 是一部分的 CSSOM（CSS 物件模型），它代表了一個 CSS 樣式表中的單一樣式規則。使用 CSSPropertyRule，開發者可以直接操作 CSS 屬性，這對於需要根據用戶操作或其他條件動態調整樣式的應用程式非常有用。

### 目的
CSSPropertyRule 的主要目的是提供一個方便的方式讓開發者能夠讀取和修改 CSS 樣式。透過這個物件，開發者能夠獲取特定 CSS 屬性的當前值，並且能夠直接更改它。

### 使用方法
在 JavaScript 中，CSSPropertyRule 主要是在透過 `CSSStyleSheet` 和 `CSSRule` 來訪問。開發者首先需要獲取到樣式表，然後通過其規則來訪問 CSSPropertyRule。

### 詳情
CSSPropertyRule 提供了以下屬性和方法：
- `style`：這是一個 CSSStyleDeclaration 物件，包含了所有 CSS 屬性。
- `selectorText`：這個屬性返回 CSS 選擇器的字串表示。
- `cssText`：這個屬性返回完整的 CSS 規則字串。

## Examples
以下是基本的使用範例：

### 例子 1：獲取 CSSPropertyRule
```javascript
let styleSheet = document.styleSheets[0];
let rule = styleSheet.cssRules[0]; // 獲取第一條規則

if (rule instanceof CSSStyleRule) {
    console.log(rule.selectorText); // 輸出選擇器
    console.log(rule.style.color); // 獲取顏色屬性的值
}
```

### 例子 2：修改 CSSPropertyRule
```javascript
let styleSheet = document.styleSheets[0];
let rule = styleSheet.cssRules[0];

if (rule instanceof CSSStyleRule) {
    rule.style.color = 'red'; // 將顏色屬性改為紅色
}
```

## Explanation
使用 CSSPropertyRule 時，有幾個常見的陷阱需要注意：
1. **規則類型檢查**：在操作 CSS 規則時，必須檢查該規則是否為 `CSSStyleRule`，否則會導致錯誤。
2. **樣式表的跨域限制**：如果樣式表來自不同的來源，則會因為同源策略而無法訪問。
3. **動態更新**：修改 CSSPropertyRule 會即時反映在頁面上，但需確保在正確的時機進行修改，以避免影響用戶體驗。

## One Line Summary
CSSPropertyRule 是一個 JavaScript 物件，允許開發者以編程方式訪問和修改 CSS 樣式規則。