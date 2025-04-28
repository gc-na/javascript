<!--
Meta Description: # JavaScript 中的 scrollX：滾動位置屬性 ## 概要 `scrollX` 是一個屬性，用於獲取或設置當前視窗的水平滾動位置。在網頁中，當用戶滾動內容時，`scrollX` 可以幫助開發者獲取當前的滾動狀態，從而在用戶界面中做出相應的調整。 ## 文檔 ### 目的 `scroll...
Meta Keywords: scrollx, window, javascript, scrollto, currentscrollx
-->

# JavaScript 中的 scrollX：滾動位置屬性

## 概要
`scrollX` 是一個屬性，用於獲取或設置當前視窗的水平滾動位置。在網頁中，當用戶滾動內容時，`scrollX` 可以幫助開發者獲取當前的滾動狀態，從而在用戶界面中做出相應的調整。

## 文檔
### 目的
`scrollX` 是 `window` 物件的一個屬性，提供了當前窗口的水平滾動距離。這個屬性通常用於檢測和控制滾動行為，特別是在需要根據滾動位置進行動態效果的情況下。

### 使用方法
要使用 `scrollX`，只需調用 `window.scrollX` 來獲取當前的水平滾動距離。如果需要設置滾動位置，可以使用 `window.scrollTo(x, y)` 方法，其中 `x` 是水平距離。

### 詳細資訊
- **類型**: 數字（以像素為單位）
- **讀取方法**: `let currentScrollX = window.scrollX;`
- **設置方法**: `window.scrollTo(x, y);`，其中 `x` 是要設置的水平滾動位置。

## 例子
### 獲取當前滾動位置
```javascript
// 獲取當前的水平滾動位置
let currentScrollX = window.scrollX;
console.log(currentScrollX);
```

### 設置滾動位置
```javascript
// 將滾動位置設置為 100 像素
window.scrollTo(100, window.scrollY);
```

### 滾動事件監聽
```javascript
// 監聽滾動事件並顯示當前的 scrollX 值
window.addEventListener('scroll', function() {
    console.log('當前 scrollX:', window.scrollX);
});
```

## 解釋
使用 `scrollX` 時需要注意以下幾點：
- 確保在網頁內容已經加載完成後再使用 `scrollX`，否則可能會獲取到不正確的值。
- `scrollX` 只會在滾動條存在時返回有效的數值，對於沒有水平滾動的元素，返回值將為 `0`。
- 在某些情況下，使用 CSS 的 `overflow` 屬性可能會影響 `scrollX` 的行為。

## 一句總結
`scrollX` 是一個用於獲取當前窗口水平滾動位置的屬性，對於創建動態和響應式網頁設計非常有用。