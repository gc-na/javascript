<!--
Meta Description: # JavaScript 中的 scrollY: 了解網頁滾動位置的關鍵屬性 ## 簡介 `scrollY` 是一個用於獲取當前頁面垂直滾動位置的屬性，屬於 `window` 物件。這個屬性對於需要動態追蹤頁面滾動狀態的網頁應用程式尤為重要。 ## 文檔 ### 目的 `scrollY` 使開發者能...
Meta Keywords: scrolly, window, javascript, currentscrolly, console
-->

# JavaScript 中的 scrollY: 了解網頁滾動位置的關鍵屬性

## 簡介
`scrollY` 是一個用於獲取當前頁面垂直滾動位置的屬性，屬於 `window` 物件。這個屬性對於需要動態追蹤頁面滾動狀態的網頁應用程式尤為重要。

## 文檔
### 目的
`scrollY` 使開發者能夠獲取用戶在頁面上垂直滾動的距離，這對於實現滾動效果、懸浮菜單以及其他基於滾動事件的交互功能非常有用。

### 使用方式
`scrollY` 的使用方法非常簡單，開發者只需通過 `window.scrollY` 來獲取當前的滾動位置。其值以像素為單位，表示頁面頂部到當前滾動位置的距離。

### 詳細信息
- 屬性類型：`number`
- 讀取屬性：`window.scrollY`（只讀）
- 返回值：返回當前垂直滾動的像素數值。

## 範例
以下是一些基本的 `scrollY` 使用範例：

### 基本範例
```javascript
// 獲取當前垂直滾動位置
let currentScrollY = window.scrollY;
console.log("當前垂直滾動位置: " + currentScrollY + " 像素");
```

### 監聽滾動事件
```javascript
window.addEventListener("scroll", function() {
    console.log("當前垂直滾動位置: " + window.scrollY + " 像素");
});
```

## 解釋
- **常見問題**：在某些情況下，如果頁面未滾動，`scrollY` 的值將為 `0`。
- **注意事項**：`scrollY` 的值只在頁面滾動時更新，因此需要搭配滾動事件來獲取實時的滾動位置。
- **相對於 `scrollX`**：`scrollY` 只關注垂直滾動，對於水平滾動使用 `scrollX`。

## 總結
`scrollY` 是一個簡單而強大的屬性，能夠讓開發者輕鬆獲取網頁的垂直滾動位置，並在網頁應用中實現各種滾動相關的功能。