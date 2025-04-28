<!--
Meta Description: # MediaQueryListEvent 在 JavaScript 中的應用 ## 簡介 MediaQueryListEvent 是一個在 JavaScript 中用來處理媒體查詢狀態變更的事件。透過這個事件，開發者可以監聽媒體查詢的變更，以便根據不同的顯示環境調整應用程序的行為或樣式。 ## 文...
Meta Keywords: mediaquerylistevent, mediaquerylist, javascript, addeventlistener, 600px
-->

# MediaQueryListEvent 在 JavaScript 中的應用

## 簡介
MediaQueryListEvent 是一個在 JavaScript 中用來處理媒體查詢狀態變更的事件。透過這個事件，開發者可以監聽媒體查詢的變更，以便根據不同的顯示環境調整應用程序的行為或樣式。

## 文檔
### 目的
MediaQueryListEvent 提供了一個機制來監聽媒體查詢的變化，讓開發者能夠在特定條件下執行相應的操作。這在響應式設計中尤其重要，因為應用程序可能需要適應不同的設備屏幕大小或方向。

### 使用方法
要使用 MediaQueryListEvent，首先需要創建一個 MediaQueryList 物件，然後添加一個監聽器來處理變更事件。以下是基本的使用步驟：

1. 創建一個 MediaQueryList 物件。
2. 使用 `addListener` 或 `addEventListener` 方法來監聽變更事件。
3. 在事件處理函數中，根據需要執行特定的操作。

### 重要細節
- 媒體查詢的變更可以是由於視窗大小改變或其他因素造成的。
- MediaQueryListEvent 物件包含一個 `matches` 屬性，表示當前媒體查詢是否匹配。
- 使用 `removeListener` 或 `removeEventListener` 可以停止監聽事件。

## 範例
### 基本使用
```javascript
// 創建一個 MediaQueryList 物件
const mediaQueryList = window.matchMedia("(max-width: 600px)");

// 定義事件處理函數
function handleMediaChange(event) {
    if (event.matches) {
        console.log("視窗小於 600px");
    } else {
        console.log("視窗大於或等於 600px");
    }
}

// 添加事件監聽器
mediaQueryList.addEventListener("change", handleMediaChange);

// 初次檢查媒體查詢狀態
handleMediaChange(mediaQueryList);
```

## 解釋
### 常見問題
- 當使用 `addListener` 方法時，請注意這是一個舊的 API，建議使用 `addEventListener` 來提高兼容性。
- 確保在不再需要監聽時移除事件監聽器，以避免內存泄漏。
- 媒體查詢的表達式需要是有效的 CSS 媒體查詢語法，否則會引發錯誤。

## 總結
MediaQueryListEvent 是一個強大的工具，幫助開發者在 JavaScript 中有效地監聽和響應媒體查詢的變化。