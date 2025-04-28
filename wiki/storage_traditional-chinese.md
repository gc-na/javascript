<!--
Meta Description: # JavaScript 儲存（Storage）功能概述 ## 簡介 JavaScript 提供了多種儲存機制，讓開發人員可以在客戶端儲存資料。這些儲存方式包括 `localStorage` 和 `sessionStorage`，它們都是 Web Storage API 的一部分，能夠有效地管理用戶...
Meta Keywords: localstorage, sessionstorage, javascript, 儲存資料, setitem
-->

# JavaScript 儲存（Storage）功能概述

## 簡介
JavaScript 提供了多種儲存機制，讓開發人員可以在客戶端儲存資料。這些儲存方式包括 `localStorage` 和 `sessionStorage`，它們都是 Web Storage API 的一部分，能夠有效地管理用戶的資料。

## 文件說明
### 目的
JavaScript 的儲存功能旨在提供一種簡單且有效的方式來存取和管理用戶的資料，無論是持久性的（`localStorage`）還是會話性的（`sessionStorage`）。

### 使用方法
- **localStorage**：用於持久性資料存儲，資料會在瀏覽器關閉後仍然存在，直到被明確刪除。
- **sessionStorage**：用於會話性資料存儲，資料僅在當前瀏覽器標籤頁開啟期間存在，關閉標籤頁後資料將會丟失。

#### 基本用法
```javascript
// 使用 localStorage 儲存資料
localStorage.setItem('key', 'value'); // 儲存資料
let value = localStorage.getItem('key'); // 讀取資料
localStorage.removeItem('key'); // 刪除資料

// 使用 sessionStorage 儲存資料
sessionStorage.setItem('sessionKey', 'sessionValue'); // 儲存資料
let sessionValue = sessionStorage.getItem('sessionKey'); // 讀取資料
sessionStorage.removeItem('sessionKey'); // 刪除資料
```

## 範例
```javascript
// 儲存用戶名稱到 localStorage
localStorage.setItem('username', 'JohnDoe');

// 從 localStorage 讀取用戶名稱
let username = localStorage.getItem('username');
console.log(username); // 輸出：JohnDoe

// 儲存會話 ID 到 sessionStorage
sessionStorage.setItem('sessionID', 'abc123');

// 從 sessionStorage 讀取會話 ID
let sessionID = sessionStorage.getItem('sessionID');
console.log(sessionID); // 輸出：abc123
```

## 解釋
### 常見陷阱
- **資料大小限制**：`localStorage` 和 `sessionStorage` 的儲存限制通常為 5MB，超出此限制會導致錯誤。
- **資料類型**：所有儲存的資料都會被轉換為字串，若需儲存物件，必須使用 `JSON.stringify()` 和 `JSON.parse()` 來轉換。
- **跨域限制**：每個域名的儲存空間是獨立的，無法跨域存取。

### 附加注意事項
- 確保在使用這些儲存功能時，遵循安全性最佳實踐，例如避免儲存敏感資訊。
- 使用 `clear()` 方法可以清空整個儲存空間（`localStorage.clear()` 或 `sessionStorage.clear()`）。

## 總結
JavaScript 的儲存功能提供了一個簡便的方式來管理客戶端資料，無論是短期還是長期，都能有效地增強用戶體驗。