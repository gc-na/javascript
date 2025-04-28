<!--
Meta Description: # visualViewport：JavaScript 中的視覺視口 API ## 簡介 `visualViewport` 是一個 JavaScript 物件，提供了對瀏覽器視口的視覺資訊。它使開發者能夠獲取視口的尺寸和位移，以便對用戶界面進行更靈活的調整，特別是在移動設備上。 ## 文檔 ### ...
Meta Keywords: visualviewport, 以像素為單位, javascript, width, height
-->

# visualViewport：JavaScript 中的視覺視口 API

## 簡介
`visualViewport` 是一個 JavaScript 物件，提供了對瀏覽器視口的視覺資訊。它使開發者能夠獲取視口的尺寸和位移，以便對用戶界面進行更靈活的調整，特別是在移動設備上。

## 文檔
### 目的
`visualViewport` 主要用於獲取和監控視口的變化，特別是在用戶滾動或縮放時。這對於創建響應式和互動式的網頁應用至關重要。

### 使用方法
要使用 `visualViewport`，只需調用 `window.visualViewport`，這樣就可以訪問其屬性和事件。常用的屬性包括 `width`、`height`、`offsetLeft`、`offsetTop` 等。

#### 屬性
- **width**：當前視口的寬度（以像素為單位）。
- **height**：當前視口的高度（以像素為單位）。
- **offsetLeft**：視口左側的偏移量（以像素為單位）。
- **offsetTop**：視口上側的偏移量（以像素為單位）。

#### 事件
- **resize**：當視口大小改變時觸發。
- **scroll**：當視口滾動時觸發。

### 範例
以下是如何使用 `visualViewport` 的基本示例：

```javascript
// 獲取視口的寬度和高度
const viewportWidth = visualViewport.width;
const viewportHeight = visualViewport.height;

console.log(`視口寬度: ${viewportWidth}, 視口高度: ${viewportHeight}`);

// 監聽 resize 事件
visualViewport.addEventListener('resize', () => {
    console.log('視口大小已改變');
});

// 監聽 scroll 事件
visualViewport.addEventListener('scroll', () => {
    console.log(`視口偏移：左側 ${visualViewport.offsetLeft}, 上側 ${visualViewport.offsetTop}`);
});
```

## 解釋
在使用 `visualViewport` 時，開發者需要注意以下幾點：
- **兼容性**：並非所有瀏覽器均支持 `visualViewport`。在使用前，應檢查瀏覽器的兼容性。
- **性能問題**：頻繁的事件觸發可能會影響性能，因此應考慮對事件進行節流或防抖處理。
- **用戶體驗**：盡量保持界面在視口變化時不會出現突兀的變化，為用戶提供流暢的體驗。

## 一句總結
`visualViewport` 是一個強大的工具，可幫助開發者獲取和管理瀏覽器視口的視覺信息，特別是在移動設備上。