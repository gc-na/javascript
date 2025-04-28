<!--
Meta Description: # JavaScript 的 outerHeight 屬性：完整指南與使用範例 ## 簡介 `outerHeight` 是一個與窗口尺寸相關的屬性，用於獲取瀏覽器窗口的外部高度（包括工具欄和滾動條等的高度）。這對於在網頁中進行自適應設計和動態布局非常有用。 ## 文檔 ### 目的 `outerHe...
Meta Keywords: outerheight, javascript, window, let, height
-->

# JavaScript 的 outerHeight 屬性：完整指南與使用範例

## 簡介
`outerHeight` 是一個與窗口尺寸相關的屬性，用於獲取瀏覽器窗口的外部高度（包括工具欄和滾動條等的高度）。這對於在網頁中進行自適應設計和動態布局非常有用。

## 文檔
### 目的
`outerHeight` 屬性主要用於獲取或設置瀏覽器窗口的外部高度，這在進行窗口尺寸相關的操作時非常重要。

### 使用方法
`outerHeight` 是 `window` 對象的一部分，通常用於獲取當前窗口的高度。其基本用法如下：

```javascript
let windowHeight = window.outerHeight;
```

### 詳細說明
- **返回值**：`outerHeight` 返回一個整數，表示窗口的外部高度（以像素為單位）。
- **注意**：此屬性隨著窗口大小的變化而變化，因此在使用時需考慮事件監聽器的設置，以便在窗口大小改變時獲取最新的高度。

## 範例
### 獲取窗口外部高度
```javascript
// 獲取當前窗口的外部高度
let height = window.outerHeight;
console.log("當前窗口的外部高度為: " + height + " 像素");
```

### 窗口調整時更新外部高度
```javascript
// 監聽窗口大小變化事件
window.addEventListener('resize', function() {
    let updatedHeight = window.outerHeight;
    console.log("調整後的窗口外部高度為: " + updatedHeight + " 像素");
});
```

## 解釋
### 常見問題與注意事項
1. **不同瀏覽器的兼容性**：雖然 `outerHeight` 在大多數主流瀏覽器中都受支持，但在某些較舊的瀏覽器中可能不完全兼容。
2. **設置與獲取**：`outerHeight` 主要用於獲取窗口的高度，直接設置此屬性在大多數情況下不會生效。
3. **與 innerHeight 的區別**：`outerHeight` 包括窗口的所有組件（如工具欄），而 `innerHeight` 僅包括文檔可見區域的高度。

## 一句總結
`outerHeight` 是一個用於獲取瀏覽器窗口外部高度的 JavaScript 屬性，對於設計響應式網頁至關重要。