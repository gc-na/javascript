<!--
Meta Description: # Request: JavaScript 中的請求處理 ## 概述 在 JavaScript 中，"Request" 主要指代發送 HTTP 請求的過程，通常用於與伺服器進行數據交換。這一過程可以通過多種方法實現，包括 Fetch API 和 XMLHttpRequest。 ## 文檔 ### 目...
Meta Keywords: fetch, xhr, api, xmlhttprequest, javascript
-->

# Request: JavaScript 中的請求處理

## 概述
在 JavaScript 中，"Request" 主要指代發送 HTTP 請求的過程，通常用於與伺服器進行數據交換。這一過程可以通過多種方法實現，包括 Fetch API 和 XMLHttpRequest。

## 文檔
### 目的
"Request" 的主要目的是向伺服器發送請求，以獲取或提交數據。JavaScript 提供多種工具來創建和管理這些請求，最常見的是 Fetch API。

### 使用方法
1. **Fetch API**:
   - 使用 `fetch()` 函數發送請求，並返回一個 Promise 對象。
   - 語法：
     ```javascript
     fetch(url, options)
     ```

   - 參數：
     - `url`: 要請求的資源的 URL。
     - `options`: 可選的配置對象，包含方法、標頭、主體等。

2. **XMLHttpRequest**:
   - 傳統的請求方法，使用 `XMLHttpRequest` 對象。
   - 主要方法：
     - `open(method, url)`: 初始化請求。
     - `send(data)`: 發送請求。
   - 示例：
     ```javascript
     const xhr = new XMLHttpRequest();
     xhr.open("GET", url);
     xhr.send();
     ```

### 詳細說明
- 使用 Fetch API 時，請求默認為 GET 方法。若需使用 POST 等其他方法，必須在 options 中設置 `method` 屬性。
- Fetch API 返回的 Promise 需要通過 `.then()` 或 `async/await` 進行處理，以獲取響應對象。
- XMLHttpRequest 需要額外處理狀態碼和錯誤，並且其語法相對繁瑣。

## 示例
### 使用 Fetch API 的基本示例
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('There was a problem with the fetch operation:', error));
```

### 使用 XMLHttpRequest 的基本示例
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data');
xhr.onload = () => {
  if (xhr.status === 200) {
    console.log(JSON.parse(xhr.responseText));
  } else {
    console.error('Request failed with status:', xhr.status);
  }
};
xhr.onerror = () => console.error('Request failed');
xhr.send();
```

## 解釋
- **常見問題**:
  - 使用 Fetch API 時，未處理的錯誤可能導致 Promise 被拒絕，因此必須添加錯誤處理。
  - XMLHttpRequest 的同步請求會阻塞主線程，影響性能，應避免使用。

- **額外提示**:
  - 確保在請求中設置正確的標頭，例如 `Content-Type`，以確保伺服器能正確解析請求數據。
  - 使用 HTTPS 確保數據安全。

## 總結
"Request" 在 JavaScript 中是一個關鍵概念，用於發送和接收數據，主要通過 Fetch API 和 XMLHttpRequest 實現。