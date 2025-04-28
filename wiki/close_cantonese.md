<!--
Meta Description: # JavaScript 的 close 方法：關閉視窗或標籤頁 ## 簡介 在 JavaScript 中，`close` 方法用於關閉瀏覽器視窗或標籤頁。這個方法通常與 `window.open` 方法一起使用，以便在創建新視窗後能夠關閉它。 ## 文檔 ### 目的 `close` 方法的主要目...
Meta Keywords: close, javascript, window, open, newwindow
-->

# JavaScript 的 close 方法：關閉視窗或標籤頁

## 簡介
在 JavaScript 中，`close` 方法用於關閉瀏覽器視窗或標籤頁。這個方法通常與 `window.open` 方法一起使用，以便在創建新視窗後能夠關閉它。

## 文檔
### 目的
`close` 方法的主要目的是關閉由 JavaScript 創建的瀏覽器視窗。需要注意的是，這個方法只能關閉由腳本打開的視窗。

### 語法
```javascript
window.close();
```

### 使用
- `close()` 方法無參數。
- 如果當前視窗並非由腳本創建，則無法使用此方法關閉。

### 詳細資訊
- 這個方法在許多瀏覽器中受安全性限制，無法隨意關閉用戶在手動打開的視窗。
- 在某些情況下，瀏覽器可能會顯示提示，確認用戶是否確實希望關閉視窗。

## 範例
以下是使用 `close` 方法的基本範例：

```javascript
// 使用 window.open 打開新視窗
var newWindow = window.open('https://www.example.com', '_blank');

// 關閉新視窗
newWindow.close();
```

## 解釋
- **常見陷阱**：如果嘗試關閉一個用戶手動打開的視窗，會出現錯誤，因為 `close` 方法只對由腳本創建的視窗有效。
- **安全性問題**：許多現代瀏覽器對於關閉視窗有嚴格的限制，以防止惡意網站自動關閉用戶的視窗。
- **使用場景**：通常在彈出窗口中使用 `close` 方法，例如在用戶完成某些操作後自動關閉該窗口。

## 一句總結
`close` 方法在 JavaScript 中用於關閉由腳本創建的瀏覽器視窗或標籤頁。