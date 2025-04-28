<!--
Meta Description: # JavaScript 中的標頭（Headers） ## 摘要 標頭（Headers）在 JavaScript 中通常用於 HTTP 請求和響應，負責傳遞額外的資訊，例如內容類型、授權資訊和快取控制等。理解標頭的使用對於開發網頁應用程式至關重要。 ## 文檔 ### 目的 標頭是 HTTP 協議中...
Meta Keywords: headers, error, data, javascript, api
-->

# JavaScript 中的標頭（Headers）

## 摘要
標頭（Headers）在 JavaScript 中通常用於 HTTP 請求和響應，負責傳遞額外的資訊，例如內容類型、授權資訊和快取控制等。理解標頭的使用對於開發網頁應用程式至關重要。

## 文檔
### 目的
標頭是 HTTP 協議中的一部分，用於提供有關請求或響應的元數據。JavaScript 常通過 `fetch` API 或 `XMLHttpRequest` 來操作這些標頭，以便與伺服器進行通訊。

### 使用
在 JavaScript 中，標頭可以用於設定請求的內容或讀取響應的元數據。使用 `fetch` API 進行 HTTP 請求時，可以使用 `Headers` 物件來操作標頭。

#### 基本用法
```javascript
// 創建一個 Headers 物件
const headers = new Headers();

// 設定標頭
headers.append('Content-Type', 'application/json');
headers.append('Authorization', 'Bearer token');

// 使用 fetch API 傳送請求
fetch('https://api.example.com/data', {
    method: 'GET',
    headers: headers
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

### 詳細描述
- **標頭類型**: HTTP 標頭分為請求標頭和響應標頭。請求標頭由客戶端發送，而響應標頭由伺服器返回。
- **常見標頭**:
  - `Content-Type`: 指定傳送的數據類型，例如 `application/json`。
  - `Authorization`: 用於身份驗證的標頭，通常包含令牌或憑證。
  - `Accept`: 指定客戶端能夠處理的內容類型。
  
透過 `fetch` API，開發者可以輕鬆地設置和讀取這些標頭。

## 範例
### 設定標頭的範例
```javascript
fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer your_token'
    },
    body: JSON.stringify({ key: 'value' })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

### 讀取響應標頭的範例
```javascript
fetch('https://api.example.com/data')
.then(response => {
    const contentType = response.headers.get('Content-Type');
    console.log('Content-Type:', contentType);
    return response.json();
})
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

## 解釋
- **常見陷阱**: 
  - 忘記設置 `Content-Type` 標頭可能會導致伺服器無法正確解析請求體。
  - 使用錯誤的標頭名稱或格式可能會導致請求失敗。
- **注意事項**:
  - 確保 API 端點支持的標頭，否則請求可能會被拒絕。
  - 在處理敏感資料時，應謹慎使用標頭，尤其是授權標頭。

## 一句話總結
在 JavaScript 中，標頭用於 HTTP 請求和響應，幫助傳遞重要的元數據。