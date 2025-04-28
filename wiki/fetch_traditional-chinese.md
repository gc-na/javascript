<!--
Meta Description: # JavaScript 的 fetch 函數：高效的網絡請求方法 ## 簡介 `fetch` 是一個現代 JavaScript API，主要用於進行網絡請求。它提供了一個簡單且強大的方法來發送 HTTP 請求，並處理響應，從而在客戶端與伺服器之間進行數據交換。 ## 文檔 ### 目的 `fetc...
Meta Keywords: fetch, response, error, javascript, data
-->

# JavaScript 的 fetch 函數：高效的網絡請求方法

## 簡介
`fetch` 是一個現代 JavaScript API，主要用於進行網絡請求。它提供了一個簡單且強大的方法來發送 HTTP 請求，並處理響應，從而在客戶端與伺服器之間進行數據交換。

## 文檔
### 目的
`fetch` 函數的主要目的是透過 Promise 來進行網絡請求，使得開發者能夠輕鬆獲取資源。它是 XMLHttpRequest 的現代替代方案，提供了更簡潔的語法和更好的可讀性。

### 用法
`fetch` 函數的基本語法如下：

```javascript
fetch(url, options)
```

- **url**：請求的資源 URL，必需。
- **options**：可選的配置對象，包括 HTTP 方法、標頭、請求體等設置。

### 返回值
`fetch` 函數返回一個 Promise，解析後將返回一個 Response 對象，該對象代表了請求的響應。

## 例子
### 基本用法
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

### POST 請求
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ key: 'value' }),
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## 解釋
### 常見的問題與注意事項
1. **CORS**：當從不同的域發送請求時，可能會遇到跨來源資源共享（CORS）問題。確保伺服器正確配置 CORS 標頭。
2. **Promise 錯誤處理**：如果網絡請求失敗，Promise 會被拒絕，這需要在 `.catch()` 中處理。
3. **響應檢查**：在處理響應之前，檢查 `response.ok` 是一個好習慣，以確保請求成功。
4. **請求方法**：確保在選項中正確設置 HTTP 方法（如 GET, POST 等）。

## 總結
`fetch` 函數是 JavaScript 中進行網絡請求的強大工具，簡化了數據獲取流程並提高了可讀性。