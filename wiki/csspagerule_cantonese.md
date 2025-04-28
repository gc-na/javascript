<!--
Meta Description: # CSSPageRule：JavaScript 操控 CSS 規則的工具 ## 簡介 CSSPageRule 是一個在 JavaScript 中用來操作 CSS 頁面規則的介面，屬於 CSSOM（CSS 物件模型）的一部分。它可讓開發者動態地讀取或修改 CSS 的頁面規則，非常適合用於創建自適應或...
Meta Keywords: csspagerule, css, javascript, page, pagerule
-->

# CSSPageRule：JavaScript 操控 CSS 規則的工具

## 簡介
CSSPageRule 是一個在 JavaScript 中用來操作 CSS 頁面規則的介面，屬於 CSSOM（CSS 物件模型）的一部分。它可讓開發者動態地讀取或修改 CSS 的頁面規則，非常適合用於創建自適應或響應式的網頁樣式。

## 文檔
### 目的
CSSPageRule 主要用來表示 CSS 中的 @page 規則。這些規則通常用於列印樣式，讓開發者能夠定義列印時的頁面設置，例如頁邊距和方向。

### 用法
要使用 CSSPageRule，開發者首先需要訪問樣式表中的規則。可以通過 `CSSStyleSheet` 物件獲取，然後檢查該規則的類型是否為 `CSSPageRule`。

```javascript
const styleSheet = document.styleSheets[0];
const pageRule = styleSheet.cssRules[0]; // 假設第一條規則為 @page
```

### 詳細信息
- **屬性**:
  - `selectorText`: 獲取或設定 @page 規則的選擇器。
  - `style`: 獲取或設定該規則的 CSSStyleDeclaration 物件，這讓開發者可以修改具體的樣式。

- **方法**: CSSPageRule 目前不提供額外的方法，主要依賴於其屬性來進行操作。

## 示例
### 基本使用示例
以下是如何使用 CSSPageRule 來修改列印樣式的示例：

```javascript
const styleSheet = document.styleSheets[0]; // 獲取第一個樣式表
const pageRule = styleSheet.cssRules[0]; // 獲取第一條規則

if (pageRule instanceof CSSPageRule) {
    console.log(pageRule.selectorText); // 輸出: @page
    pageRule.style.margin = '1in'; // 設定頁面邊距
}
```

## 解釋
在使用 CSSPageRule 時，開發者應注意以下幾點：
- **兼容性**: 某些舊版瀏覽器可能不支援 CSSPageRule，建議在使用前進行檢查。
- **規則位置**: 確保 @page 規則在樣式表中的正確位置，否則可能會無法正確獲取。
- **動態更新**: 修改 CSSPageRule 時，變更會立即影響到所有使用該樣式的元素。

## 一句總結
CSSPageRule 是一個強大的工具，讓開發者能夠在 JavaScript 中動態管理和修改 CSS 的列印樣式規則。