<!--
Meta Description: # JavaScript 中的 StyleSheet：操作樣式表的全面指南 ## 簡介 在 JavaScript 中，`StyleSheet` 是一個用於管理和操作 CSS 樣式的對象，允許開發者動態地改變網頁的外觀和感覺。透過操作樣式表，開發者可以在運行時添加、修改或刪除樣式。 ## 文檔 `St...
Meta Keywords: stylesheet, javascript, css, document, stylesheets
-->

# JavaScript 中的 StyleSheet：操作樣式表的全面指南

## 簡介
在 JavaScript 中，`StyleSheet` 是一個用於管理和操作 CSS 樣式的對象，允許開發者動態地改變網頁的外觀和感覺。透過操作樣式表，開發者可以在運行時添加、修改或刪除樣式。

## 文檔
`StyleSheet` 是由瀏覽器提供的一個接口，代表一組 CSS 規則。它通常與文檔的 `<style>` 標籤或外部 CSS 檔案相關聯。開發者可以通過 JavaScript 訪問和修改這些規則，以便實現動態樣式變更。

### 目的
使用 `StyleSheet` 對象，可以在網頁加載後，根據需要調整樣式，這對於創建交互式和響應式的用戶界面非常重要。

### 用法
在 JavaScript 中，你可以通過 `document.styleSheets` 獲取當前文檔的所有樣式表。每個樣式表都有其 `cssRules` 屬性，該屬性包含了一組 CSS 規則。

```javascript
// 獲取第一個樣式表
const styleSheet = document.styleSheets[0];

// 獲取樣式規則
const rules = styleSheet.cssRules;

// 修改第一個規則的顏色
rules[0].style.color = 'red';
```

## 示例
以下是一些基本用法的示例：

### 添加樣式規則
```javascript
const styleSheet = document.styleSheets[0];

// 添加新的 CSS 規則
styleSheet.insertRule('body { background-color: blue; }', styleSheet.cssRules.length);
```

### 刪除樣式規則
```javascript
const styleSheet = document.styleSheets[0];

// 刪除第一個 CSS 規則
styleSheet.deleteRule(0);
```

### 修改樣式規則
```javascript
const styleSheet = document.styleSheets[0];

// 修改第一個規則的字體大小
styleSheet.cssRules[0].style.fontSize = '20px';
```

## 解釋
在使用 `StyleSheet` 時，有幾個常見的陷阱和注意事項：

1. **跨域問題**：如果你的樣式表來自不同的域，瀏覽器將不允許你訪問其 `cssRules`，這是由於同源政策的限制。
2. **性能考量**：頻繁地添加和刪除樣式規則可能會影響性能，因此應謹慎使用。
3. **樣式優先級**：當修改樣式時，確保理解 CSS 的優先級規則，否則更改可能不會如預期般顯示。

## 總結
`StyleSheet` 是一個強大的工具，讓開發者能夠在 JavaScript 中靈活地操作和控制網頁的樣式。