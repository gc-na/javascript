<!--
Meta Description: # MediaList：JavaScript 中的媒體列表管理 ## 概述 `MediaList` 是一個 JavaScript 介面，主要用於操作和管理 CSS 媒體查詢列表。它允許開發者透過 JavaScript 動態地添加、刪除或修改媒體查詢，從而影響樣式表的呈現。 ## 文檔 ### 目的 ...
Meta Keywords: medialist, javascript, css, media, 媒體查詢
-->

# MediaList：JavaScript 中的媒體列表管理

## 概述
`MediaList` 是一個 JavaScript 介面，主要用於操作和管理 CSS 媒體查詢列表。它允許開發者透過 JavaScript 動態地添加、刪除或修改媒體查詢，從而影響樣式表的呈現。

## 文檔
### 目的
`MediaList` 的主要目的是提供一個方便的方式來操作 CSS 媒體查詢，讓開發者可以根據不同的媒體條件動態調整頁面樣式。這對於響應式設計尤為重要。

### 使用方法
`MediaList` 是 `CSSStyleSheet` 接口的一部分，主要用於訪問和修改媒體查詢。使用 `media` 屬性可以獲取或設置 `MediaList`。

#### 屬性
- `media`: 返回一個 `MediaList` 對象，包含該樣式表的媒體查詢。

#### 方法
- `appendMedium(medium)`: 將新的媒體查詢添加到列表中。
- `deleteMedium(medium)`: 從列表中刪除指定的媒體查詢。

### 詳細信息
`MediaList` 提供的媒體查詢可以包含各種條件，例如視窗尺寸、設備類型等。開發者可以利用這些媒體查詢來控制樣式表的應用。

## 示例
以下是使用 `MediaList` 的基本範例：

```javascript
// 獲取樣式表
let stylesheet = document.styleSheets[0];

// 獲取媒體列表
let mediaList = stylesheet.media;

// 顯示當前媒體查詢
console.log(mediaList.mediaText);

// 添加新的媒體查詢
mediaList.appendMedium('(max-width: 600px)');

// 刪除特定的媒體查詢
mediaList.deleteMedium('(max-width: 800px)');
```

## 解釋
在使用 `MediaList` 時，開發者需要注意以下幾點：
- 不同瀏覽器的兼容性：在使用之前，檢查目標瀏覽器是否支持 `MediaList` 接口。
- 媒體查詢的格式必須正確，否則會導致錯誤。
- 進行修改後，樣式的應用可能不會立即反映，因此需要確保樣式表的更新流程正確。

## 一句總結
`MediaList` 是 JavaScript 中一個強大的工具，允許開發者動態管理和操作 CSS 媒體查詢，從而提升網頁的響應式設計能力。