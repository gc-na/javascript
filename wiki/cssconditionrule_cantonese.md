<!--
Meta Description: # CSSConditionRule：JavaScript 中的 CSS 條件規則 ## 簡介 CSSConditionRule 是一個 JavaScript 接口，用於表示 CSS 中的條件規則，例如媒體查詢或支持某些特性時的樣式規則。它允許開發者在 JavaScript 中動態訪問和修改 CSS...
Meta Keywords: cssconditionrule, css, javascript, cssrules, rules
-->

# CSSConditionRule：JavaScript 中的 CSS 條件規則

## 簡介
CSSConditionRule 是一個 JavaScript 接口，用於表示 CSS 中的條件規則，例如媒體查詢或支持某些特性時的樣式規則。它允許開發者在 JavaScript 中動態訪問和修改 CSS 規則，從而實現更靈活的樣式管理。

## 文檔
### 目的
CSSConditionRule 主要用於操作 CSS 中的條件規則，這些規則通常以 `@media` 或 `@supports` 開頭。通過這個接口，開發者可以在 JavaScript 中檢索和修改這些條件規則，以適應不同的設備或條件。

### 使用方法
要使用 CSSConditionRule，首先需要獲取一個樣式表中的規則。這可以通過 `document.styleSheets` 獲得。然後，可以遍歷樣式表中的規則，檢查每個規則是否為 CSSConditionRule。

### 詳細信息
- **屬性**：
  - `conditionText`：返回該條件規則的條件文本（例如，媒體查詢的條件）。
  - `cssRules`：返回一個 CSSRuleList，這個列表包含該條件下的所有 CSS 規則。

- **方法**：
  - `deleteRule(index)`：從條件規則中刪除指定索引的規則。
  - `insertRule(rule, index)`：在指定索引插入一條新的 CSS 規則。

## 示例
### 基本用法
以下是如何使用 CSSConditionRule 的基本示例：

```javascript
// 獲取第一個樣式表
let styleSheet = document.styleSheets[0];

// 獲取所有規則
let rules = styleSheet.cssRules;

// 遍歷規則
for (let i = 0; i < rules.length; i++) {
    if (rules[i] instanceof CSSConditionRule) {
        console.log('條件文本:', rules[i].conditionText);
        console.log('CSS 規則:', rules[i].cssRules);
    }
}
```

### 插入和刪除規則
以下示例展示如何插入和刪除條件規則：

```javascript
// 假設有一個 @media 規則
let mediaRule = rules[0]; // 假設這是 @media 規則
mediaRule.insertRule('body { background-color: lightblue; }', mediaRule.cssRules.length);
console.log('更新後的規則:', mediaRule.cssRules);

mediaRule.deleteRule(0); // 刪除第一條規則
console.log('刪除後的規則:', mediaRule.cssRules);
```

## 解釋
在使用 CSSConditionRule 時，開發者需要注意以下幾點：
- 確保在操作 CSS 規則時，樣式表已經正確加載。
- 不同瀏覽器對於 CSSConditionRule 的支持可能會有所不同，建議檢查兼容性。
- 使用 `deleteRule` 和 `insertRule` 時，必須確保索引在有效範圍內，否則會引發錯誤。
- 對於動態樣式的應用，需考慮性能影響，避免過於頻繁的操作。

## 一句總結
CSSConditionRule 是一個強大的工具，讓開發者能夠在 JavaScript 中靈活管理和操作 CSS 條件規則。