<!--
Meta Description: # JavaScript 的 innerHeight 屬性：全方位指南 ## 摘要 `innerHeight` 是一個在 JavaScript 中用來獲取瀏覽器視窗的內部高度的屬性，該高度不包括工具列和滾動條。這個屬性對於響應式設計和動態布局非常有用。 ## 文檔 ### 目的 `window.in...
Meta Keywords: innerheight, window, height, javascript, resize
-->

# JavaScript 的 innerHeight 屬性：全方位指南

## 摘要
`innerHeight` 是一個在 JavaScript 中用來獲取瀏覽器視窗的內部高度的屬性，該高度不包括工具列和滾動條。這個屬性對於響應式設計和動態布局非常有用。

## 文檔
### 目的
`window.innerHeight` 屬性返回當前視窗的內部高度（以像素為單位），包含了縱向的滾動條，但不包括瀏覽器的工具列和滾動條。

### 使用方式
要使用 `innerHeight` 屬性，只需訪問 `window` 對象。其基本語法如下：

```javascript
let height = window.innerHeight;
```

### 詳細說明
- **返回值**: 返回一個整數，表示視窗的高度。
- **類型**: 整數（Number）。
- **適用範圍**: 此屬性在所有主流瀏覽器中均可使用，並且在移動設備上也有良好的支持。
- **更改檢測**: `innerHeight` 的值會隨著視窗大小的改變而變化，這使得它適合用於事件監聽器中，例如 `resize` 事件。

## 範例
### 基本使用
以下是一個簡單的範例，用於獲取並顯示當前視窗的內部高度：

```javascript
// 獲取視窗的內部高度
let height = window.innerHeight;
console.log("當前視窗的內部高度是: " + height + " 像素");
```

### 在 Resize 事件中使用
可以在 `resize` 事件中使用 `innerHeight` 來動態更新元素的樣式：

```javascript
window.addEventListener('resize', function() {
    let height = window.innerHeight;
    document.getElementById('myDiv').style.height = height + 'px';
});
```

## 解釋
### 常見問題
- **在不同的設備上**: `innerHeight` 可能在不同的設備和瀏覽器中顯示不同的值，特別是在移動設備上，因為設備的工具列和地址欄會影響可見的內容區域。
- **滾動條的影響**: 在某些瀏覽器中，如果出現了縱向滾動條，`innerHeight` 會包含滾動條的高度。如果需要考慮這一點，可能需要額外計算。

### 附加注意事項
- 在頁面加載完成前，使用 `innerHeight` 可能會得到不正確的值。確保在 DOMContentLoaded 事件後使用它。

## 一行總結
`innerHeight` 屬性可用於獲取當前瀏覽器視窗的內部高度，是響應式設計中不可或缺的工具。