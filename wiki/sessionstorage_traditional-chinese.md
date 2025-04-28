<!--
Meta Description: # sessionStorage：JavaScript 的會話儲存解決方案 ## 摘要 `sessionStorage` 是一個 Web 存儲 API，允許開發者在用戶的瀏覽器中以鍵值對的形式儲存數據，並且這些數據僅在當前會話中可用，關閉瀏覽器後數據將被清除。 ## 文檔 `sessionStora...
Meta Keywords: sessionstorage, username, key, javascript, setitem
-->

# sessionStorage：JavaScript 的會話儲存解決方案

## 摘要
`sessionStorage` 是一個 Web 存儲 API，允許開發者在用戶的瀏覽器中以鍵值對的形式儲存數據，並且這些數據僅在當前會話中可用，關閉瀏覽器後數據將被清除。

## 文檔
`sessionStorage` 提供了一種簡單的方式來儲存資料在用戶的瀏覽器中，與 `localStorage` 相比，`sessionStorage` 的數據僅在當前瀏覽器標籤頁的會話期間有效。

### 目的
- 儲存用戶的臨時資料，例如表單輸入或用戶選擇的設置。
- 提高用戶體驗，允許在多個頁面間保持狀態。

### 用法
`sessionStorage` 物件具有以下方法和屬性：

- `setItem(key, value)`：將指定的鍵值對儲存到 `sessionStorage`。
- `getItem(key)`：根據指定的鍵獲取對應的值。
- `removeItem(key)`：根據指定的鍵刪除對應的項目。
- `clear()`：清空所有的 `sessionStorage` 數據。
- `key(index)`：根據索引獲取指定的鍵名稱。
- `length`：儲存在 `sessionStorage` 中的項目數量。

### 詳細使用範例
```javascript
// 儲存數據
sessionStorage.setItem('username', 'john_doe');

// 獲取數據
const username = sessionStorage.getItem('username');
console.log(username); // 輸出: john_doe

// 刪除特定項目
sessionStorage.removeItem('username');

// 清空所有數據
sessionStorage.clear();
```

## 解釋
在使用 `sessionStorage` 時，有幾個常見的注意事項：
1. **範圍限制**：`sessionStorage` 僅在同一標籤頁中可用，無法在不同的標籤頁或窗口間共享數據。
2. **數據大小限制**：大多數瀏覽器對 `sessionStorage` 的存儲容量有上限，通常為 5MB。
3. **數據類型**：`sessionStorage` 僅能儲存字串類型，若要存儲物件或數組，需使用 `JSON.stringify()` 進行序列化，讀取時需使用 `JSON.parse()` 反序列化。
4. **跨域問題**：`sessionStorage` 只能在同一域名下使用，無法跨域訪問。

## 一句總結
`sessionStorage` 是 JavaScript 提供的一種方便的方式，用於在瀏覽器會話中儲存和管理數據。