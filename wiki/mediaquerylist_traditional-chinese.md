<!--
Meta Description: # MediaQueryList 在 JavaScript 中的使用指南 ## 簡介 `MediaQueryList` 是一個在 JavaScript 中用於監聽和檢測媒體查詢狀態的接口。它使開發者能夠根據瀏覽器視窗的大小及其他媒體屬性，動態地調整網頁內容的顯示。 ## 文檔 ### 目的 `Med...
Meta Keywords: mediaquerylist, javascript, window, matchmedia, addlistener
-->

# MediaQueryList 在 JavaScript 中的使用指南

## 簡介
`MediaQueryList` 是一個在 JavaScript 中用於監聽和檢測媒體查詢狀態的接口。它使開發者能夠根據瀏覽器視窗的大小及其他媒體屬性，動態地調整網頁內容的顯示。

## 文檔
### 目的
`MediaQueryList` 的主要目的是提供一種機制，讓開發者能夠根據不同的媒體查詢來執行特定的 JavaScript 代碼。這在響應式設計中特別有用，因為它可以根據不同的顯示設備或視窗大小，調整網站的樣式和功能。

### 使用方式
`MediaQueryList` 可以通過 `window.matchMedia()` 方法來創建。該方法接受一個媒體查詢字符串作為參數，並返回一個 `MediaQueryList` 對象。

#### 語法
```javascript
const mediaQueryList = window.matchMedia(mediaQueryString);
```

#### 參數
- `mediaQueryString`：一個描述媒體查詢的字符串，例如 `"(max-width: 600px)"`。

### 屬性與方法
- **matches**：返回一個布林值，指示當前文檔是否符合媒體查詢。
- **media**：返回媒體查詢的字符串。
- **addListener(callback)**：註冊一個回調函數，以便在媒體查詢狀態改變時執行。
- **removeListener(callback)**：移除先前註冊的回調函數。

## 範例
### 基本用法
以下是一個簡單的例子，展示如何使用 `MediaQueryList` 來檢測視窗大小。

```javascript
const mediaQueryList = window.matchMedia("(max-width: 600px)");

function handleMediaQueryChange(event) {
    if (event.matches) {
        console.log("視窗寬度小於或等於 600 像素");
    } else {
        console.log("視窗寬度大於 600 像素");
    }
}

// 註冊事件監聽器
mediaQueryList.addListener(handleMediaQueryChange);

// 初始檢查
handleMediaQueryChange(mediaQueryList);
```

## 解釋
### 常見問題與注意事項
- **性能考量**：在添加大量的媒體查詢監聽器時，可能會影響效能，因此建議只在必要時使用。
- **相容性**：在某些舊版本的瀏覽器中，`addListener` 和 `removeListener` 方法可能不被支持，應考慮使用 `addEventListener` 來監聽變化。
- **移除監聽器**：在不再需要監聽的情況下，應及時移除監聽器以避免不必要的資源消耗。

## 一句總結
`MediaQueryList` 是一個強大的工具，讓開發者可以根據媒體查詢動態調整網頁內容，提高用戶體驗。