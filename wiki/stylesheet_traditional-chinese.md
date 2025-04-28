<!--
Meta Description: # JavaScript 中的樣式表 (StyleSheet) 指令 ## 概述 在 JavaScript 中，樣式表 (StyleSheet) 是用於動態操作和管理網頁樣式的重要工具。透過 JavaScript，開發者能夠增刪樣式、調整 CSS 屬性以及在需要時即時更新網頁的外觀。 ## 文件說明...
Meta Keywords: stylesheet, javascript, stylesheets, document, const
-->

# JavaScript 中的樣式表 (StyleSheet) 指令

## 概述
在 JavaScript 中，樣式表 (StyleSheet) 是用於動態操作和管理網頁樣式的重要工具。透過 JavaScript，開發者能夠增刪樣式、調整 CSS 屬性以及在需要時即時更新網頁的外觀。

## 文件說明
樣式表 (StyleSheet) 是一個物件，通常與 Document Object Model (DOM) 一同使用。它允許開發者透過 JavaScript 來控制和修改網頁的 CSS 樣式。這對於創建互動式和響應式的用戶界面至關重要。

### 目的
使用樣式表，開發者可以：
- 動態改變網頁的樣式。
- 根據用戶操作或事件來調整樣式。
- 實現主題切換或其他視覺反饋。

### 使用方式
要使用樣式表，開發者可以透過 `document.styleSheets` 訪問當前文檔中的樣式表。這是一個樣式表物件的集合，開發者可以對其進行添加、刪除或修改的操作。

```javascript
// 獲取所有樣式表
const stylesheets = document.styleSheets;

// 獲取第一個樣式表
const firstStylesheet = stylesheets[0];

// 添加一個新的樣式規則
firstStylesheet.insertRule('body { background-color: lightblue; }', firstStylesheet.cssRules.length);
```

## 範例
以下是使用 JavaScript 動態操作樣式表的基本範例：

### 添加新樣式
```javascript
// 選擇第一個樣式表並添加新樣式
const stylesheet = document.styleSheets[0];
stylesheet.insertRule('h1 { color: red; }', stylesheet.cssRules.length);
```

### 刪除樣式
```javascript
// 刪除第一個樣式表中的第一個樣式規則
const stylesheet = document.styleSheets[0];
stylesheet.deleteRule(0);
```

### 修改樣式
```javascript
// 修改第一個樣式表中的第一個樣式規則
const stylesheet = document.styleSheets[0];
stylesheet.cssRules[0].style.color = 'blue';
```

## 解釋
在使用樣式表時，開發者可能會遇到一些常見的陷阱：
- **跨瀏覽器兼容性**：某些規則可能在不同的瀏覽器中行為不一致，因此需進行測試。
- **樣式優先級**：新添加的樣式規則可能會被現有的樣式覆蓋，理解 CSS 的優先級規則至關重要。
- **性能考量**：動態修改樣式可能影響性能，尤其是在大量 DOM 元素上進行操作時，建議批量處理。

## 一句話總結
樣式表 (StyleSheet) 是 JavaScript 中用於動態管理和修改網頁樣式的重要工具，使開發者能夠創建更具互動性和吸引力的用戶界面。