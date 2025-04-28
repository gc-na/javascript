<!--
Meta Description: # CSSMediaRule：JavaScript 中的媒體規則操作 ## 簡介 CSSMediaRule 是 JavaScript 中的接口，允許開發者對 CSS 媒體規則進行讀取和操作。這些媒體規則使得樣式能夠根據不同的媒體類型和特性進行調整，例如螢幕大小或設備類型。透過 CSSMediaRul...
Meta Keywords: cssmediarule, javascript, css, stylesheet, let
-->

# CSSMediaRule：JavaScript 中的媒體規則操作

## 簡介
CSSMediaRule 是 JavaScript 中的接口，允許開發者對 CSS 媒體規則進行讀取和操作。這些媒體規則使得樣式能夠根據不同的媒體類型和特性進行調整，例如螢幕大小或設備類型。透過 CSSMediaRule，開發者可以動態管理和修改 CSS 樣式以增強用戶體驗。

## 文檔
### 目的
CSSMediaRule 主要用於操作 CSS 中的媒體查詢規則，開發者可以在 JavaScript 中創建、修改或刪除這些規則，以適應不同的顯示條件。

### 使用方法
CSSMediaRule 在 JavaScript 中主要通過 `CSSStyleSheet` 的 `insertRule` 和 `deleteRule` 方法來創建和刪除媒體規則。這些方法允許開發者編輯樣式表中的 CSS 規則。

#### 屬性和方法
- **media**: 返回一個 `MediaList` 對象，描述這個媒體規則適用的媒體類型。
- **cssText**: 返回該規則的完整 CSS 文本。
- **insertRule(rule, index)**: 在指定索引位置插入新的規則。
- **deleteRule(index)**: 刪除指定索引位置的規則。

## 範例
### 基本用法
以下是如何使用 CSSMediaRule 的範例：

```javascript
// 獲取樣式表
let stylesheet = document.styleSheets[0];

// 插入新的媒體規則
let mediaRule = '@media (max-width: 600px) { body { background-color: lightblue; } }';
stylesheet.insertRule(mediaRule, stylesheet.cssRules.length);

// 獲取媒體規則
let rules = stylesheet.cssRules;
for (let i = 0; i < rules.length; i++) {
    if (rules[i] instanceof CSSMediaRule) {
        console.log(rules[i].cssText);
    }
}

// 刪除媒體規則
stylesheet.deleteRule(stylesheet.cssRules.length - 1);
```

## 解釋
### 常見陷阱和注意事項
1. **跨瀏覽器兼容性**: 確保在使用 CSSMediaRule 時檢查瀏覽器的兼容性，某些舊版瀏覽器可能不支持。
2. **順序問題**: 插入新規則時，注意規則的順序，因為後插入的規則可能會覆蓋先前的規則。
3. **性能考量**: 大量動態操作樣式表可能會影響性能，最佳做法是盡量減少樣式的即時修改。

## 總結
CSSMediaRule 是一個強大的工具，允許開發者在 JavaScript 中動態管理 CSS 媒體規則，以促進響應式設計和用戶體驗的優化。