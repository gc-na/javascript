<!--
Meta Description: # JavaScript 嘅 fetch 函數：一個全面嘅指南 ## 簡介 `fetch` 函數係 JavaScript 提供嘅一個現代化 API，用於進行網絡請求，從伺服器獲取資源。佢以 Promise 為基礎，提供一個簡單嘅方法去處理異步請求。 ## 文檔 `fetch` 函數嘅主要目的是向伺服...
Meta Keywords: fetch, response, error, javascript, data
-->

# JavaScript 嘅 fetch 函數：一個全面嘅指南

## 簡介
`fetch` 函數係 JavaScript 提供嘅一個現代化 API，用於進行網絡請求，從伺服器獲取資源。佢以 Promise 為基礎，提供一個簡單嘅方法去處理異步請求。

## 文檔
`fetch` 函數嘅主要目的是向伺服器發送請求，並接收回應。佢嘅基本語法如下：

```javascript
fetch(url, options)
```

- **url**: 要請求嘅資源 URL。
- **options**: 一個可選嘅配置對象，包含請求嘅方法、標頭、主體等信息。

### 使用方法
`fetch` 函數返回一個 Promise，當請求完成時，Promise 會解析為 Response 對象。要從 Response 中提取數據，通常需要調用相應嘅方法，如 `json()`、`text()` 或 `blob()`。

### 詳細信息
- **默認方法**: `GET`。
- **支持 CORS**: 允許跨域請求。
- **錯誤處理**: 需要手動檢查 HTTP 狀態碼，因為非 200 的狀態不會自動拒絕 Promise。

## 範例
### 基本用法
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('網絡響應出錯');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('Fetch 錯誤:', error));
```

### POST 請求
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ key: 'value' })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Fetch 錯誤:', error));
```

## 解釋
在使用 `fetch` 時，開發者需要留意以下幾點：
- **錯誤處理**: 需要手動檢查 HTTP 狀態碼，如 `response.ok`，否則會錯過非 200 的錯誤。
- **CORS 限制**: 跨域請求可能會受到 CORS 政策限制，需確保伺服器允許跨域請求。
- **瀏覽器相容性**: 雖然大部分現代瀏覽器都支持 `fetch`，但舊版本或某些瀏覽器可能需要 polyfill。

## 一句總結
`fetch` 函數係 JavaScript 中進行網絡請求嘅現代方法，提供簡潔嘅 API 來處理異步數據請求。