<!--
Meta Description: # CSSStyleSheet：JavaScript 中操作 CSS 樣式表的關鍵對象 ## 簡介 `CSSStyleSheet` 是一個 JavaScript 對象，用於表示和操作瀏覽器中的 CSS 樣式表。它能夠讓開發者動態地添加、刪除或修改 CSS 規則，從而影響網頁的外觀和樣式。 ## 文檔...
Meta Keywords: css, cssstylesheet, javascript, stylesheets, firststylesheet
-->

# CSSStyleSheet：JavaScript 中操作 CSS 樣式表的關鍵對象

## 簡介
`CSSStyleSheet` 是一個 JavaScript 對象，用於表示和操作瀏覽器中的 CSS 樣式表。它能夠讓開發者動態地添加、刪除或修改 CSS 規則，從而影響網頁的外觀和樣式。

## 文檔
`CSSStyleSheet` 對象是當前文檔中的 CSS 樣式表的表示。這個對象提供了多種方法和屬性來控制 CSS 規則的應用。使用 `document.styleSheets` 可以獲取網頁中所有的樣式表，然後可以進一步通過 `CSSStyleSheet` 對象來訪問每一個樣式表的詳細信息。

### 主要用途
- **動態修改樣式**：可以通過 JavaScript 修改現有的 CSS 規則，或添加新的規則。
- **刪除樣式**：能夠移除不再需要的 CSS 規則。
- **檢查樣式**：可以檢查和獲取現有的 CSS 規則和樣式屬性。

### 使用方法
`CSSStyleSheet` 的常用屬性和方法包括：
- `cssRules`：返回一個 `CSSRule` 對象的集合，表示樣式表中的所有規則。
- `insertRule(rule, index)`：在指定位置插入一條新的 CSS 規則。
- `deleteRule(index)`：刪除指定位置的 CSS 規則。

## 範例
以下是如何使用 `CSSStyleSheet` 的基本範例：

### 1. 獲取樣式表
```javascript
const styleSheets = document.styleSheets;
const firstStyleSheet = styleSheets[0]; // 獲取第一個樣式表
```

### 2. 插入新的 CSS 規則
```javascript
firstStyleSheet.insertRule('body { background-color: lightblue; }', firstStyleSheet.cssRules.length);
```

### 3. 刪除 CSS 規則
```javascript
firstStyleSheet.deleteRule(0); // 刪除第一條規則
```

## 解釋
使用 `CSSStyleSheet` 時需注意以下幾點：
- **跨域問題**：如果樣式表來自不同的域，則無法訪問其內容，這是由於同源政策的限制。
- **索引問題**：在刪除規則時，必須注意索引的正確性，因為刪除規則會改變後續規則的索引位置。
- **性能考量**：頻繁地插入和刪除規則可能會影響性能，建議批量操作。

## 一句總結
`CSSStyleSheet` 是 JavaScript 中用來動態操作 CSS 樣式表的強大工具。