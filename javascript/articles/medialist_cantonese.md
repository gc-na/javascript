<!--
Meta Description: # MediaList 在 JavaScript 中的使用 ## 簡介 `MediaList` 是一個 JavaScript 介面，主要用於處理 CSS 媒體查詢的列表。這個介面允許開發者動態地訪問和修改媒體查詢，從而在不同設備上靈活調整樣式。 ## 文檔 `MediaList` 介面提供了操作媒體...
Meta Keywords: medialist, javascript, let, media, length
-->

# MediaList 在 JavaScript 中的使用

## 簡介
`MediaList` 是一個 JavaScript 介面，主要用於處理 CSS 媒體查詢的列表。這個介面允許開發者動態地訪問和修改媒體查詢，從而在不同設備上靈活調整樣式。

## 文檔
`MediaList` 介面提供了操作媒體查詢的功能，特別是在 CSS 中使用 `@media` 規則。這使得開發者能夠獲取當前媒體查詢的條件，並根據需要進行增刪改查。每個 `MediaList` 實例都包含多個媒體條件，這些條件可以透過 JavaScript 進行訪問和修改。

### 主要屬性和方法
- **`length`**: 返回 `MediaList` 中媒體條件的數量。
- **`item(index)`**: 根據索引返回指定的媒體條件。
- **`appendMedium(medium)`**: 將新的媒體條件附加到列表末尾。
- **`deleteMedium(medium)`**: 從列表中刪除指定的媒體條件。

### 使用情境
`MediaList` 介面的主要用例包括動態改變樣式，適應不同的顯示設備，例如在移動設備上隱藏某些元素，或在桌面上顯示額外的信息。

## 範例
以下是幾個基本的使用範例，展示如何使用 `MediaList` 介面：

### 獲取媒體條件
```javascript
let mediaList = window.matchMedia("(max-width: 600px)");
console.log(mediaList.media); // 輸出: "(max-width: 600px)"
```

### 修改媒體條件
```javascript
let styleSheet = document.styleSheets[0];
let mediaList = styleSheet.media;

console.log(mediaList.length); // 輸出媒體條件數量
mediaList.appendMedium("(min-width: 800px)"); // 添加新的媒體條件
console.log(mediaList.length); // 現在的媒體條件數量
```

### 刪除媒體條件
```javascript
let styleSheet = document.styleSheets[0];
let mediaList = styleSheet.media;

mediaList.deleteMedium("(max-width: 600px)"); // 刪除指定的媒體條件
console.log(mediaList.length); // 更新後的媒體條件數量
```

## 解釋
在使用 `MediaList` 時，開發者需要注意以下幾點：
- 媒體條件的格式必須正確，否則將無法添加或刪除。
- 不同瀏覽器對於 `MediaList` 的支持程度可能有所不同，建議在使用前檢查相容性。
- 動態修改媒體查詢後，可能需要手動觸發樣式更新，以確保新的樣式生效。

## 一行總結
`MediaList` 介面允許開發者在 JavaScript 中動態管理和修改 CSS 媒體查詢。