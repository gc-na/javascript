<!--
Meta Description: # CSSStyleDeclaration 在 JavaScript 中的使用指南 ## 概述 `CSSStyleDeclaration` 是一個 JavaScript 介面，用於表示 HTML 元素的樣式屬性。它提供了對 CSS 樣式的訪問和修改能力，使開發者能夠動態地調整網頁的外觀。 ## 文檔...
Meta Keywords: box, cssstyledeclaration, javascript, style, css
-->

# CSSStyleDeclaration 在 JavaScript 中的使用指南

## 概述
`CSSStyleDeclaration` 是一個 JavaScript 介面，用於表示 HTML 元素的樣式屬性。它提供了對 CSS 樣式的訪問和修改能力，使開發者能夠動態地調整網頁的外觀。

## 文檔
`CSSStyleDeclaration` 介面是 DOM 的一部分，通常通過 `element.style` 屬性獲取。它包含了元素的內聯樣式，並可以用來讀取和設定 CSS 屬性。

### 目的
`CSSStyleDeclaration` 使開發者能夠直接操作元素的樣式，而無需編輯 CSS 檔案。這對於在運行時根據用戶互動或其他條件改變樣式非常有用。

### 使用方式
要使用 `CSSStyleDeclaration`，首先需要獲取一個元素的樣式。這可以通過以下方式實現：

```javascript
const element = document.getElementById('myElement');
const styles = element.style;
```

接下來，可以通過屬性名稱讀取或設定樣式：

```javascript
// 設定樣式
styles.color = 'red';
styles.backgroundColor = 'blue';

// 獲取樣式
console.log(styles.color); // 輸出: red
```

### 詳細說明
`CSSStyleDeclaration` 介面支持多種屬性操作，包括：
- 讀取現有的 CSS 屬性
- 設定新的 CSS 屬性
- 移除 CSS 屬性
- 使用 `setProperty` 方法來設置屬性及其優先級

## 範例
以下是一些基本的使用範例：

### 設定樣式
```javascript
const box = document.getElementById('box');
box.style.width = '100px';
box.style.height = '100px';
box.style.backgroundColor = 'green';
```

### 獲取樣式
```javascript
const box = document.getElementById('box');
console.log(box.style.width); // 輸出: 100px
```

### 使用 setProperty 方法
```javascript
const box = document.getElementById('box');
box.style.setProperty('border', '1px solid black', 'important');
```

## 解釋
- **注意事項**：`CSSStyleDeclaration` 只處理內聯樣式，對於從外部樣式表或 `<style>` 標籤中繼承的樣式，無法直接通過此介面訪問。
- **常見錯誤**：在設置屬性時，需使用駝峰式命名法。例如，`background-color` 應寫為 `backgroundColor`。
- **獲取未設定的屬性**：如果嘗試獲取未設定的屬性，將返回空字串，而不是 `null`。

## 單行摘要
`CSSStyleDeclaration` 介面允許 JavaScript 直接讀取和修改 HTML 元素的內聯樣式屬性。