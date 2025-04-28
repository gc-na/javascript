<!--
Meta Description: # CSSMediaRule：JavaScript 中的 CSS 媒體規則 ## 概述 CSSMediaRule 是一個 JavaScript 介面，用於表示 CSS 樣式表中的媒體查詢規則。這些規則根據特定的媒體類型或狀態（如螢幕大小或設備類型）來應用樣式，使得網頁在不同設備上更具響應性。 ## ...
Meta Keywords: cssmediarule, css, javascript, let, stylesheet
-->

# CSSMediaRule：JavaScript 中的 CSS 媒體規則

## 概述
CSSMediaRule 是一個 JavaScript 介面，用於表示 CSS 樣式表中的媒體查詢規則。這些規則根據特定的媒體類型或狀態（如螢幕大小或設備類型）來應用樣式，使得網頁在不同設備上更具響應性。

## 文檔
CSSMediaRule 允許開發者動態訪問和操作 CSS 樣式表中的媒體查詢。這個介面屬於 CSSOM（CSS 物件模型），它提供了對 CSS 樣式的編程接口。使用 CSSMediaRule，開發者可以：

- 獲取媒體查詢的條件。
- 讀取和修改包含的樣式規則。
- 動態添加或刪除媒體規則。

### 使用方法
要使用 CSSMediaRule，首先需要獲取一個樣式表或者文檔中的 CSS 規則。然後，可以檢查該規則是否為 CSSMediaRule 的實例。

### 主要屬性和方法
- **media**：返回或設置媒體查詢的條件。
- **cssRules**：返回該媒體規則包含的所有 CSS 規則。
- **appendRule(rule)**：向媒體規則中添加新的 CSS 規則。
- **deleteRule(index)**：刪除指定索引的 CSS 規則。

## 範例
以下是 CSSMediaRule 的基本使用範例：

```javascript
// 獲取第一個樣式表
let stylesheet = document.styleSheets[0];

// 獲取 CSS 規則
let rules = stylesheet.cssRules;

// 遍歷所有規則
for (let i = 0; i < rules.length; i++) {
    if (rules[i] instanceof CSSMediaRule) {
        console.log(rules[i].media.mediaText); // 輸出媒體查詢條件
    }
}
```

### 添加媒體規則的範例
```javascript
let newMediaRule = '@media (max-width: 600px) { body { background-color: lightblue; } }';
stylesheet.insertRule(newMediaRule, stylesheet.cssRules.length);
```

## 解釋
在使用 CSSMediaRule 時，有一些常見的陷阱需要注意：

1. **跨域問題**：如果樣式表來自不同的來源，則無法訪問其規則，這是由於瀏覽器的安全策略。
2. **動態更新**：在動態添加或刪除規則時，應確保正確處理索引，以避免 IndexError。
3. **瀏覽器支持**：某些較舊的瀏覽器可能不完全支持 CSSOM 或 CSSMediaRule。

## 一行總結
CSSMediaRule 使開發者能夠在 JavaScript 中動態操作 CSS 媒體查詢規則，以提高網頁的響應性和可訪問性。