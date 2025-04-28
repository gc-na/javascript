<!--
Meta Description: # scrollX：JavaScript 中的水平滾動屬性 ## 簡介 `scrollX` 是一個屬性，屬於 `window` 物件，用於獲取或設定當前頁面在水平方向上的滾動距離。它可以幫助開發者監控和控制滾動行為，提升用戶體驗。 ## 文件說明 ### 目的 `scrollX` 用於獲得當前滾動條...
Meta Keywords: scrollx, window, javascript, scrollto, currentscrollx
-->

# scrollX：JavaScript 中的水平滾動屬性

## 簡介
`scrollX` 是一個屬性，屬於 `window` 物件，用於獲取或設定當前頁面在水平方向上的滾動距離。它可以幫助開發者監控和控制滾動行為，提升用戶體驗。

## 文件說明
### 目的
`scrollX` 用於獲得當前滾動條在水平方向上已滾動的像素數。這對於需要根據滾動位置更新頁面內容或效果的應用程式非常有用。

### 使用方式
`scrollX` 可以直接通過 `window.scrollX` 訪問，無需任何參數。當用於設定時，請使用 `window.scrollTo(x, y)` 方法來更改滾動位置。

### 詳細說明
- **返回值**：`scrollX` 返回一個整數，表示當前水平滾動距離（以像素為單位）。
- **讀取**：使用 `let currentScrollX = window.scrollX;` 可以獲取當前的水平滾動值。
- **設定**：若需設定滾動位置，應使用 `window.scrollTo(x, y)` 方法，其中 `x` 為新的水平滾動值。

## 範例
### 獲取水平滾動距離
```javascript
let currentScrollX = window.scrollX;
console.log("當前水平滾動距離: " + currentScrollX + " 像素");
```

### 設定水平滾動位置
```javascript
// 將滾動位置設定為 200 像素
window.scrollTo(200, window.scrollY);
```

## 解釋
- **常見陷阱**：有時，開發者可能會錯誤地使用 `scrollLeft` 屬性來獲取滾動距離，這僅適用於 DOM 元素，而不適用於 `window`。
- **注意事項**：在某些情況下，頁面可能會有 CSS 屬性影響滾動行為，例如 `overflow: hidden`，這可能導致 `scrollX` 的值不如預期。

## 總結
`scrollX` 是一個簡單而強大的工具，用於獲取當前頁面在水平方向上的滾動距離，能夠助力開發者優化用戶界面。