<!--
Meta Description: # CSSStyleRule 於 JavaScript 中的應用與實作 ## 概述 `CSSStyleRule` 是一個代表 CSS 樣式規則的物件，允許開發者使用 JavaScript 動態地讀取和修改樣式表中的樣式規則。它是 Web 開發中操作 CSS 的關鍵組件之一。 ## 文檔 `CSSSt...
Meta Keywords: javascript, const, stylesheet, cssstylerule, css
-->

# CSSStyleRule 於 JavaScript 中的應用與實作

## 概述
`CSSStyleRule` 是一個代表 CSS 樣式規則的物件，允許開發者使用 JavaScript 動態地讀取和修改樣式表中的樣式規則。它是 Web 開發中操作 CSS 的關鍵組件之一。

## 文檔
`CSSStyleRule` 屬於 CSSOM (CSS 物件模型)，主要用來表示樣式表中的單個規則。每個 `CSSStyleRule` 物件都包含一組樣式屬性和選擇器，開發者可以透過 JavaScript 進行以下操作：

- **獲取選擇器**: 使用 `selectorText` 屬性來獲取該規則的選擇器。
- **獲取及設置樣式**: 使用 `style` 屬性來訪問和修改樣式屬性，如 `color`、`margin` 等。
- **應用於 DOM 元素**: 可以動態地更改樣式，從而影響網頁元素的外觀。

### 使用方法
使用 `CSSStyleRule` 需要先獲取到 CSS 樣式表，再從中選擇特定的規則。例如：

```javascript
const styleSheet = document.styleSheets[0]; // 獲取第一個樣式表
const rules = styleSheet.cssRules; // 獲取所有樣式規則

// 獲取第一條規則
const firstRule = rules[0];

// 獲取選擇器
console.log(firstRule.selectorText);

// 修改顏色屬性
firstRule.style.color = 'red';
```

## 範例
以下是一些基本的使用範例：

### 例子 1: 獲取樣式規則
```javascript
const styleSheet = document.styleSheets[0];
const rules = styleSheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    console.log(rules[i].selectorText); // 輸出所有選擇器
}
```

### 例子 2: 修改樣式屬性
```javascript
const styleSheet = document.styleSheets[0];
const firstRule = styleSheet.cssRules[0];

firstRule.style.backgroundColor = 'blue'; // 設置背景顏色為藍色
```

### 例子 3: 刪除樣式規則
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.deleteRule(0); // 刪除第一條規則
```

## 解釋
在使用 `CSSStyleRule` 的過程中，開發者有時可能會遇到一些常見的陷阱：

- **跨域問題**: 如果樣式表來自不同的域名，則無法訪問該樣式表的規則，這是出於安全考量。
- **樣式優先順序**: 當修改樣式時，要注意 CSS 的優先順序，可能會導致某些樣式無法生效。
- **不支持某些屬性**: 並非所有 CSS 屬性都可以被 JavaScript 動態修改，某些屬性需要特定的格式。

## 總結
`CSSStyleRule` 是一個允許開發者操作和修改 CSS 樣式規則的強大工具，通過 JavaScript 可以靈活地改變網頁的外觀與感受。