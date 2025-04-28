<!--
Meta Description: # AbortController：JavaScript 中的取消請求控制器 ## 摘要 `AbortController` 是一個內建的 JavaScript 物件，可用於取消網路請求或其他異步操作，提供開發者控制請求的能力，提升用戶體驗。 ## 文檔 `AbortController` 是一個用...
Meta Keywords: abortcontroller, signal, fetch, javascript, response
-->

# AbortController：JavaScript 中的取消請求控制器

## 摘要
`AbortController` 是一個內建的 JavaScript 物件，可用於取消網路請求或其他異步操作，提供開發者控制請求的能力，提升用戶體驗。

## 文檔
`AbortController` 是一個用於管理和取消異步請求的接口，最常與 Fetch API 一起使用。此控制器可以創建一個 `AbortSignal`，用來監聽請求是否被取消。當請求被取消時，相關的回調函數會被觸發，並且請求會被終止。

### 目的
使用 `AbortController` 可以有效地管理網路請求，防止不必要的請求在用戶不再需要時繼續進行，從而節省資源和改善性能。

### 用法
1. 創建一個 `AbortController` 實例。
2. 使用 `signal` 屬性傳遞 `AbortSignal` 物件到 Fetch 請求中。
3. 調用 `abort()` 方法來取消請求。

### 主要屬性及方法
- `signal`: 返回一個 `AbortSignal` 物件，這個物件用於與請求的取消狀態進行通信。
- `abort()`: 觸發取消信號，將所有與之關聯的請求標記為取消狀態。

## 範例
```javascript
// 創建 AbortController 實例
const controller = new AbortController();
const signal = controller.signal;

// 發送 Fetch 請求，並傳遞 signal
fetch('https://api.example.com/data', { signal })
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('請求已被取消');
    } else {
      console.error('請求失敗:', err);
    }
  });

// 在某些條件下取消請求
setTimeout(() => {
  controller.abort(); // 取消請求
  console.log('取消了請求');
}, 2000);
```

## 解釋
- **常見問題**: 在使用 `AbortController` 之前，請務必確保您正在使用支持它的瀏覽器（如 Chrome、Firefox 和 Edge）。某些舊版本的瀏覽器可能不支持此功能。
- **注意事項**: 如果請求被取消，Fetch API 的 Promise 會被 reject，並且錯誤的名稱將是 `AbortError`。應用程式需要處理這種情況以提高用戶體驗。
- **性能考量**: 使用 `AbortController` 可以減少不必要的網路請求，特別是在用戶快速進行操作時（例如在輸入框中快速輸入）。

## 一行總結
`AbortController` 允許開發者輕鬆地取消網路請求，提高了 JavaScript 應用程式的性能和用戶體驗。