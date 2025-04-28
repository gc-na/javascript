<!--
Meta Description: # matchMedia：JavaScript 的媒體查詢功能 ## 摘要 `matchMedia` 是一個 JavaScript 方法，允許開發者檢查媒體查詢的狀態，並針對不同的設備特徵（如螢幕寬度、高度等）來執行特定的腳本或樣式。 ## 文件說明 `matchMedia` 是一個屬於 `Wind...
Meta Keywords: matchmedia, javascript, 600px, listener, addeventlistener
-->

# matchMedia：JavaScript 的媒體查詢功能

## 摘要
`matchMedia` 是一個 JavaScript 方法，允許開發者檢查媒體查詢的狀態，並針對不同的設備特徵（如螢幕寬度、高度等）來執行特定的腳本或樣式。

## 文件說明
`matchMedia` 是一個屬於 `Window` 介面的方法，主要用於測試 CSS 媒體查詢的結果，並返回一個 `MediaQueryList` 物件。這個物件可以用來獲取媒體查詢的當前狀態，並監聽其變化，以便在設備特徵改變時進行相應的處理。

### 語法
```javascript
window.matchMedia(mediaQueryString);
```

### 參數
- `mediaQueryString`: 一個字串，表示媒體查詢的條件，例如 `"(max-width: 600px)"`。

### 返回值
返回一個 `MediaQueryList` 物件，其中包含以下屬性：
- `matches`: 一個布林值，表示媒體查詢是否符合當前的設備特徵。
- `media`: 返回傳入的媒體查詢字串。
- `addListener(listener)`: 用於監聽媒體查詢的變化（已棄用，建議使用 `addEventListener`）。
- `removeListener(listener)`: 用於移除監聽（已棄用，建議使用 `removeEventListener`）。
- `addEventListener(type, listener)`: 用於添加事件監聽器，以響應媒體查詢的變化。
- `removeEventListener(type, listener)`: 用於移除事件監聽器。

## 範例
### 基本用法
以下是一個使用 `matchMedia` 的基本範例：
```javascript
const mediaQuery = window.matchMedia('(max-width: 600px)');

function handleMediaChange(e) {
    if (e.matches) {
        console.log('視窗寬度小於或等於 600px');
    } else {
        console.log('視窗寬度大於 600px');
    }
}

// 初始檢查
handleMediaChange(mediaQuery);

// 監聽媒體查詢的變化
mediaQuery.addEventListener('change', handleMediaChange);
```

## 解釋
使用 `matchMedia` 時，開發者應注意以下幾點：
- 確保傳入的媒體查詢字串是有效的，否則會導致錯誤。
- `addListener` 和 `removeListener` 方法已被棄用，建議使用 `addEventListener` 和 `removeEventListener`。
- 在監聽器中執行的操作應避免造成性能問題，特別是在頻繁變化的情況下，例如調整視窗大小。

## 一句總結
`matchMedia` 是一個有用的 JavaScript 方法，能夠根據媒體查詢的結果來執行不同的邏輯，從而提升網站的響應式設計性能。