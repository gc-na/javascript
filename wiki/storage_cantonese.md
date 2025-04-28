<!--
Meta Description: # JavaScript 存儲：全面指南 ## 概述 JavaScript 存儲是指在網頁應用中保存和管理數據的能力，主要通過 Web Storage API，包括 Local Storage 和 Session Storage，以便在用戶會話中或跨會話中持久化數據。 ## 文檔 ### 目的 Ja...
Meta Keywords: storage, local, session, javascript, sessionstorage
-->

# JavaScript 存儲：全面指南

## 概述
JavaScript 存儲是指在網頁應用中保存和管理數據的能力，主要通過 Web Storage API，包括 Local Storage 和 Session Storage，以便在用戶會話中或跨會話中持久化數據。

## 文檔
### 目的
JavaScript 存儲的主要目的是提供一種簡單的方式來儲存用戶資料，例如偏好設置、表單數據和其他應用狀態，從而改善用戶體驗。

### 用法
JavaScript 存儲主要由以下兩個部分組成：

1. **Local Storage**: 用於永久儲存數據，數據在瀏覽器關閉後仍然存在。
2. **Session Storage**: 用於在單個瀏覽器會話中儲存數據，當標籤頁或瀏覽器關閉時，數據將被清除。

以下是如何使用這兩者的基本方法：

```javascript
// 使用 Local Storage
localStorage.setItem('key', 'value'); // 儲存數據
let value = localStorage.getItem('key'); // 獲取數據
localStorage.removeItem('key'); // 刪除數據

// 使用 Session Storage
sessionStorage.setItem('sessionKey', 'sessionValue'); // 儲存數據
let sessionValue = sessionStorage.getItem('sessionKey'); // 獲取數據
sessionStorage.removeItem('sessionKey'); // 刪除數據
```

### 詳情
- **Local Storage** 的最大容量通常是 5MB，並且可以跨頁面訪問。
- **Session Storage** 的容量也約為 5MB，但只能在同一個標籤頁或窗口中訪問。
- 存儲的數據都是字串格式，若需儲存對象，需使用 `JSON.stringify()` 轉換，並在取用時使用 `JSON.parse()` 解析。

## 示例
以下是一些基本的使用示例：

```javascript
// 儲存用戶名到 Local Storage
localStorage.setItem('username', 'JohnDoe');

// 從 Local Storage 獲取用戶名
let username = localStorage.getItem('username');
console.log(username); // 輸出：JohnDoe

// 使用 Session Storage 儲存過渡數據
sessionStorage.setItem('tempData', 'temporary value');
console.log(sessionStorage.getItem('tempData')); // 輸出：temporary value

// 清除 Session Storage 中的數據
sessionStorage.removeItem('tempData');
```

## 解釋
- **常見陷阱**: 記住 Local Storage 和 Session Storage 的數據都是字串格式，直接儲存對象會導致讀取時出現錯誤。
- **數據安全性**: 存儲在 Local Storage 和 Session Storage 的數據是以明文形式保存的，注意不要存儲敏感信息，如密碼或個人識別信息。
- **瀏覽器兼容性**: 雖然大多數現代瀏覽器都支持 Web Storage API，但在使用之前最好檢查瀏覽器的支持情況。

## 單行摘要
JavaScript 存儲允許開發者使用 Local Storage 和 Session Storage 來輕鬆儲存和管理用戶數據。