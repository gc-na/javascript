<!--
Meta Description: # JavaScript 中的請求 (Request): 完整指南 ## 概要 在 JavaScript 中，請求（Request）是與伺服器進行通信的關鍵功能。透過請求，我們可以從伺服器獲取資料或向伺服器發送資料。在前端開發中，這通常是使用 `XMLHttpRequest` 或 `fetch` A...
Meta Keywords: response, data, fetch, api, javascript
-->

# JavaScript 中的請求 (Request): 完整指南

## 概要
在 JavaScript 中，請求（Request）是與伺服器進行通信的關鍵功能。透過請求，我們可以從伺服器獲取資料或向伺服器發送資料。在前端開發中，這通常是使用 `XMLHttpRequest` 或 `fetch` API 來實現的。

## 文檔
請求的主要目的是讓客戶端（例如網頁或應用程式）能夠與伺服器進行互動。這包括但不限於：
- 獲取資料（GET 請求）
- 發送資料（POST 請求）
- 更新資料（PUT/PATCH 請求）
- 刪除資料（DELETE 請求）

### 使用方法
在 JavaScript 中，最常用的兩種請求方法是：
1. **XMLHttpRequest**：這是一個舊的 API，用於發送和接收網絡請求。
2. **Fetch API**：這是現代的網絡請求方法，更加簡潔且基於 Promise。

### 基本語法
#### 使用 Fetch API
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

#### 使用 XMLHttpRequest
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
    console.log(JSON.parse(xhr.responseText));
  }
};
xhr.send();
```

## 例子
### 獲取資料
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data));
```

### 發送資料
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ key: 'value' }),
})
.then(response => response.json())
.then(data => console.log(data));
```

### 錯誤處理
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .catch(error => console.error('Error:', error));
```

## 解釋
在使用請求時，有一些常見的陷阱或注意事項：
- **跨域請求**：當你嘗試從不同的來源獲取資料時，可能會遇到 CORS（跨來源資源共享）問題。必須確保伺服器允許跨域請求。
- **Promise 錯誤處理**：如果使用 `fetch`，記得處理 Promise 的錯誤情況，否則可能會因為未捕獲的錯誤導致應用崩潰。
- **資料格式**：確保發送和接收的資料格式一致，例如在發送 JSON 資料時，必須設置正確的 `Content-Type` 標頭。

## 一句總結
在 JavaScript 中，請求是與伺服器互動的基本手段，主要通過 `fetch` API 或 `XMLHttpRequest` 來實現。