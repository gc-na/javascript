<!--
Meta Description: # sessionStorage 在 JavaScript 中的應用 ## 簡介 `sessionStorage` 是一種 Web 存儲機制，允許在用戶的瀏覽器中以鍵值對的形式存儲數據，並且這些數據在同一個會話中有效，會話結束後數據將會被清除。 ## 文檔 `sessionStorage` 是 HT...
Meta Keywords: sessionstorage, javascript, username, key, web
-->

# sessionStorage 在 JavaScript 中的應用

## 簡介
`sessionStorage` 是一種 Web 存儲機制，允許在用戶的瀏覽器中以鍵值對的形式存儲數據，並且這些數據在同一個會話中有效，會話結束後數據將會被清除。

## 文檔
`sessionStorage` 是 HTML5 引入的 Web 存儲 API 的一部分。它提供了一種簡單的方式來存儲和檢索數據，且數據只在當前的瀏覽器標籤頁或窗口中有效。與 `localStorage` 不同，`sessionStorage` 的數據在瀏覽器關閉或標籤頁關閉後會被刪除。

### 主要功能：
- 數據只在當前會話中存儲，並在關閉標籤頁或瀏覽器時被清除。
- 每個標籤頁有自己的 `sessionStorage`，不同標籤頁之間的數據不會共享。
- 支持各種數據類型，包括字符串、數字及對象（需轉換為字符串）。

### 使用語法：
```javascript
sessionStorage.setItem(key, value); // 儲存數據
let value = sessionStorage.getItem(key); // 獲取數據
sessionStorage.removeItem(key); // 刪除特定的數據
sessionStorage.clear(); // 清空所有數據
```

## 示例
### 儲存和獲取數據
```javascript
// 儲存數據
sessionStorage.setItem('username', 'JohnDoe');

// 獲取數據
let username = sessionStorage.getItem('username');
console.log(username); // 輸出: JohnDoe
```

### 刪除數據
```javascript
// 刪除特定的數據
sessionStorage.removeItem('username');

// 清空所有數據
sessionStorage.clear();
```

## 解釋
使用 `sessionStorage` 時，開發者應注意以下幾點：
- **數據的持久性**：`sessionStorage` 僅在當前會話中有效，適合存儲會話相關的數據，如表單臨時數據。
- **數據大小限制**：不同瀏覽器對 `sessionStorage` 的大小限制不同，通常在 5MB 左右。
- **安全性**：儘量避免存儲敏感數據，因為 `sessionStorage` 的數據可以被 JavaScript 讀取，存在一定的安全風險。
- **錯誤處理**：在獲取數據時，若鍵不存在將返回 `null`，需進行適當的錯誤處理。

## 一句總結
`sessionStorage` 是一個方便的工具，用於在單一瀏覽器會話中存儲和管理數據。