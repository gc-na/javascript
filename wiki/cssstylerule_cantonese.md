<!--
Meta Description: # CSSStyleRule：JavaScript 中的 CSS 樣式規則 ## 簡介 CSSStyleRule 是一個代表 CSS 樣式規則的接口，允許 JavaScript 操作和修改 CSS 樣式。透過 CSSStyleRule，開發者可以有選擇性地更改網頁元素的樣式，增強其交互性和動態效果。...
Meta Keywords: cssstylerule, css, javascript, firstrule, const
-->

# CSSStyleRule：JavaScript 中的 CSS 樣式規則

## 簡介
CSSStyleRule 是一個代表 CSS 樣式規則的接口，允許 JavaScript 操作和修改 CSS 樣式。透過 CSSStyleRule，開發者可以有選擇性地更改網頁元素的樣式，增強其交互性和動態效果。

## 文檔
CSSStyleRule 是 CSSOM（CSS 物件模型）的一部分，主要用於表示一個完整的 CSS 樣式規則。這些規則通常在樣式表中定義，並可以透過 JavaScript 進行操作。CSSStyleRule 主要提供以下功能：

- **選擇器**：使用 `selectorText` 屬性獲取或設置與該樣式規則相關聯的選擇器。
- **樣式屬性**：使用 `style` 屬性來訪問和修改該規則的具體樣式屬性。
- **優先級**：可以透過 `cssText` 獲取或設置該規則的完整 CSS 文本。

### 使用方法
要使用 CSSStyleRule，首先你需要獲取樣式表中的某個規則，然後就可以更改它的屬性或選擇器。例如：

```javascript
const stylesheet = document.styleSheets[0];
const rules = stylesheet.cssRules;

// 假設我們要修改第一個規則
const firstRule = rules[0];

// 獲取選擇器
console.log(firstRule.selectorText); // 輸出選擇器

// 修改樣式
firstRule.style.color = 'red'; // 將文字顏色設為紅色
```

## 示例
以下是一個基本的例子，展示如何使用 CSSStyleRule 來修改樣式：

```javascript
// 獲取第一個樣式表
const stylesheet = document.styleSheets[0];

// 獲取所有規則
const rules = stylesheet.cssRules;

// 修改第一個規則的樣式
if (rules.length > 0) {
    const firstRule = rules[0];
    console.log(`原始選擇器：${firstRule.selectorText}`);
    
    // 修改背景顏色
    firstRule.style.backgroundColor = 'blue'; 
    console.log(`新的選擇器：${firstRule.selectorText}，背景顏色已更改為藍色`);
}
```

## 解釋
在使用 CSSStyleRule 時，開發者需要注意以下幾點：

- **瀏覽器兼容性**：雖然大多數主流瀏覽器均支持 CSSStyleRule，但仍然建議檢查特定版本的兼容性。
- **CSS 規則的優先級**：當修改樣式時，如果有其他樣式表或內聯樣式與之衝突，可能會導致預期的效果無法實現。
- **動態更新**：若動態添加或刪除樣式規則，可能需要重新檢查和調整 JavaScript 代碼。

## 一句總結
CSSStyleRule 允許 JavaScript 操作 CSS 樣式規則，為網頁提供更高的靈活性和動態效果。