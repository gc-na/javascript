<!--
Meta Description: # JavaScript 中的 innerHeight 屬性：網頁視窗高度 ## 概述 `innerHeight` 是一個屬性，用於獲取當前瀏覽器視窗的可見高度（以像素為單位），不包括工具欄或滾動條。這在設計響應式網頁時非常有用，可以確保內容適合不同屏幕大小。 ## 文檔 ### 目的 `inner...
Meta Keywords: innerheight, window, javascript, let, console
-->

# JavaScript 中的 innerHeight 屬性：網頁視窗高度

## 概述
`innerHeight` 是一個屬性，用於獲取當前瀏覽器視窗的可見高度（以像素為單位），不包括工具欄或滾動條。這在設計響應式網頁時非常有用，可以確保內容適合不同屏幕大小。

## 文檔
### 目的
`innerHeight` 屬性屬於 `window` 物件，提供了當前視窗的高度。這有助於開發者根據用戶的視窗大小來調整布局或執行某些功能。

### 用法
要使用 `innerHeight`，只需通過 `window.innerHeight` 訪問它。例如：

```javascript
let viewportHeight = window.innerHeight;
console.log(`當前視窗高度為：${viewportHeight}px`);
```

### 詳細信息
- **返回值**：`innerHeight` 返回一個整數，代表可見視窗的高度（以像素為單位）。
- **更新**：當視窗大小改變時，`innerHeight` 的值會自動更新。這意味著在窗口調整大小的事件中，您可以再次調用 `innerHeight` 來獲取新的高度。
- **兼容性**：`innerHeight` 在所有現代瀏覽器中都受支持，包括 Chrome、Firefox、Edge 和 Safari。

## 範例
### 基本用法
以下範例顯示如何使用 `innerHeight` 來獲取並顯示視窗高度：

```javascript
function displayViewportHeight() {
    let height = window.innerHeight;
    console.log(`當前視窗高度為：${height}px`);
}

displayViewportHeight();
```

### 窗口大小變更時獲取高度
可以監聽 `resize` 事件，實時獲取視窗高度：

```javascript
window.addEventListener('resize', () => {
    let newHeight = window.innerHeight;
    console.log(`新的視窗高度為：${newHeight}px`);
});
```

## 解釋
### 常見陷阱
- **與 scrollY 相關**：`innerHeight` 只計算可見區域的高度，不包括滾動條的高度。這意味著如果頁面內容超出視窗，`innerHeight` 不會包含滾動條的高度。
- **多個顯示器**：在使用多顯示器的環境中，`innerHeight` 可能會有所不同，具體取決於當前活動窗口的顯示器位置。

### 附加注意事項
- 在某些情況下，例如當使用全螢幕模式時，`innerHeight` 可能會返回不同的值。確保在使用時考慮這些情況。
- `innerHeight` 也不包括瀏覽器的地址欄和工具欄的高度，這些是 UI 元素。

## 總結
`innerHeight` 是一個方便的屬性，用於獲取當前瀏覽器視窗的可見高度，對於創建響應式設計尤為重要。