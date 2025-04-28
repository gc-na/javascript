<!--
Meta Description: # 緩存 (Cache) 在 JavaScript 中的應用 ## 概述 緩存是一種技術，用來提高應用程序性能，通過在記憶體中保存曾經使用過的數據來減少重複計算和資源消耗。在 JavaScript 中，緩存可用於優化網絡請求、本地存儲和資源管理。 ## 文檔 緩存的主要目的是提高數據存取速度和減少延...
Meta Keywords: cache, javascript, storage, http, local
-->

# 緩存 (Cache) 在 JavaScript 中的應用

## 概述
緩存是一種技術，用來提高應用程序性能，通過在記憶體中保存曾經使用過的數據來減少重複計算和資源消耗。在 JavaScript 中，緩存可用於優化網絡請求、本地存儲和資源管理。

## 文檔
緩存的主要目的是提高數據存取速度和減少延遲。JavaScript 提供了數種緩存技術，最常見的包括：

1. **HTTP 緩存**：利用瀏覽器的緩存機制，減少網絡請求。
2. **Service Workers**：能在客戶端攔截請求並從緩存中提供響應。
3. **Local Storage 和 Session Storage**：允許在用戶的瀏覽器中存儲數據。

### 用法
- **HTTP 緩存**：設置適當的 HTTP 標頭（如 `Cache-Control` 和 `Expires`）來指導瀏覽器如何緩存資源。
- **Service Workers**：使用 `Cache API` 來存儲和檢索請求及響應。
- **Local Storage**：使用 `localStorage.setItem(key, value)` 和 `localStorage.getItem(key)` 來存儲和檢索數據。

## 範例
下面是一些緩存的基本用法示例：

### HTTP 緩存示例
```javascript
fetch('https://api.example.com/data', {
    method: 'GET',
    headers: {
        'Cache-Control': 'max-age=3600' // 緩存一小時
    }
})
.then(response => response.json())
.then(data => console.log(data));
```

### Service Worker 緩存示例
```javascript
self.addEventListener('install', (event) => {
    event.waitUntil(
        caches.open('my-cache').then((cache) => {
            return cache.addAll([
                '/index.html',
                '/styles.css',
                '/script.js'
            ]);
        })
    );
});
```

### Local Storage 示例
```javascript
// 儲存數據
localStorage.setItem('username', 'JohnDoe');

// 獲取數據
const username = localStorage.getItem('username');
console.log(username); // 輸出: JohnDoe
```

## 解釋
使用緩存時需注意以下幾點：
- **過期時間**：設置合理的過期時間來避免使用過期數據。
- **數據一致性**：若數據經常變化，應考慮如何保持緩存與後端數據的一致性。
- **儲存限制**：Local Storage 和 Session Storage 有大小限制（通常為 5MB），需謹慎使用。

## 一句總結
緩存是 JavaScript 中提高性能的重要技術，通過妥善使用可顯著改善應用的響應速度和用戶體驗。