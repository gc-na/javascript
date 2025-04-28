<!--
Meta Description: # CSSPageRule：JavaScript 中的 CSS 規則操作 ## 簡介 CSSPageRule 是一個用於操作 CSS 規則的 JavaScript 介面，主要用於在 CSS 中定義和修改頁面樣式。它允許開發者在動態樣式表中添加、刪除和修改 CSS 規則，對於需要根據不同條件調整樣式的...
Meta Keywords: csspagerule, stylesheet, css, cssrules, javascript
-->

# CSSPageRule：JavaScript 中的 CSS 規則操作

## 簡介
CSSPageRule 是一個用於操作 CSS 規則的 JavaScript 介面，主要用於在 CSS 中定義和修改頁面樣式。它允許開發者在動態樣式表中添加、刪除和修改 CSS 規則，對於需要根據不同條件調整樣式的應用尤為重要。

## 文檔
### 目的
CSSPageRule 介面提供了一種方法來訪問和操作頁面規則，這些規則通常是在 @page 內定義的。這使得開發者能夠更靈活地控制印刷樣式或特定頁面的樣式。

### 使用方法
CSSPageRule 主要用於 CSS 樣式表中的 @page 規則。開發者可以透過 JavaScript 來讀取或修改這些規則。以下是 CSSPageRule 的主要屬性和方法：

- **selectorText**：用於獲取或設定 CSS 規則的選擇器文本。
- **style**：返回一個 CSSStyleDeclaration 物件，表示該規則的樣式屬性。
- **deleteRule()**：用於刪除當前的 CSS 規則。
- **insertRule()**：在當前規則前插入新的 CSS 規則。

### 詳細說明
CSSPageRule 是 CSSRule 的一個子類，專門針對 @page 規則進行操作。開發者可以使用 CSSStyleSheet 物件來訪問樣式表，然後使用 rules 或 cssRules 屬性來獲取包括 CSSPageRule 在內的所有規則。

```javascript
let stylesheet = document.styleSheets[0]; // 獲取第一個樣式表
let pageRule = stylesheet.cssRules[0]; // 獲取第一條規則（假設是 @page 規則）
```

通過這些屬性和方法，開發者可以動態地修改樣式表，從而適應不同的需求。

## 範例
以下是使用 CSSPageRule 的簡單範例：

### 基本範例
```javascript
let stylesheet = document.styleSheets[0]; // 獲取第一個樣式表
if (stylesheet.cssRules) {
    for (let i = 0; i < stylesheet.cssRules.length; i++) {
        if (stylesheet.cssRules[i] instanceof CSSPageRule) {
            console.log(stylesheet.cssRules[i].selectorText); // 輸出 @page 規則的選擇器
            stylesheet.cssRules[i].style.margin = "1in"; // 修改邊距
        }
    }
}
```

### 插入新規則
```javascript
let stylesheet = document.styleSheets[0];
if (stylesheet.insertRule) {
    // 插入新的 @page 規則
    stylesheet.insertRule("@page { margin: 2in; }", stylesheet.cssRules.length);
}
```

## 解釋
在使用 CSSPageRule 時，開發者應注意以下幾點：

1. **相容性**：並非所有瀏覽器都完全支持 CSSPageRule，因此在使用前應檢查其相容性。
2. **樣式表的讀取順序**：當多個樣式表存在時，規則的優先級取決於其在樣式表中的位置。
3. **性能考量**：在頻繁修改樣式的情況下，應考慮性能，避免過度操作 DOM。

## 一句總結
CSSPageRule 是一個強大的工具，用於在 JavaScript 中動態操作和控制 CSS 的頁面規則。