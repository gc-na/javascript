<!--
Meta Description: # JavaScript 中的 Response 物件：深入解析與實作範例 ## 概述 在 JavaScript 中，`Response` 物件是 Fetch API 的一部分，用於表示對網絡請求的回應。它提供了多種方法和屬性，以便於開發者獲取並處理響應數據。 ## 文檔 ### 目的 `Respo...
Meta Keywords: response, fetch, api, json, text
-->

# JavaScript 中的 Response 物件：深入解析與實作範例

## 概述
在 JavaScript 中，`Response` 物件是 Fetch API 的一部分，用於表示對網絡請求的回應。它提供了多種方法和屬性，以便於開發者獲取並處理響應數據。

## 文檔
### 目的
`Response` 物件主要用於處理來自網絡請求的響應數據。這些響應可以是文本、JSON、Blob、圖片等多種格式。

### 使用方法
`Response` 物件通常是由 `fetch()` 方法返回的。使用 Fetch API 進行網絡請求後，你可以通過該物件來訪問響應標頭、狀態碼和響應主體。

#### 基本語法
```javascript
fetch(url)
  .then(response => {
    // 使用 Response 物件
  });
```

### 屬性與方法
- **status**: 返回 HTTP 狀態碼（例如 200、404 等）。
- **statusText**: 返回狀態碼的文本描述。
- **headers**: 返回一個 Headers 物件，用於訪問響應標頭。
- **ok**: 一個布林值，表示請求是否成功（狀態碼在 200 到 299 之間）。
- **json()**: 返回解析為 JSON 的響應主體。
- **text()**: 返回響應的文本內容。
- **blob()**: 返回響應的 Blob 物件。
- **formData()**: 返回響應的 FormData 對象。

## 範例
### 基本用法
以下是一個基本的使用 `Response` 物件的例子，從 API 獲取 JSON 數據：

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok ' + response.statusText);
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('There has been a problem with your fetch operation:', error);
  });
```

### 取得文本響應
下面的範例展示了如何獲取文本響應：

```javascript
fetch('https://api.example.com/text')
  .then(response => response.text())
  .then(text => {
    console.log(text);
  });
```

## 解釋
### 常見陷阱
1. **狀態碼處理**: 許多開發者在處理 `Response` 物件時忽略了檢查 `ok` 屬性，這可能導致未處理的錯誤響應。
2. **異步處理**: 確保在調用 `json()`、`text()` 等方法時，先確認響應已成功返回，否則會引發異常。
3. **CORS 問題**: 當請求跨域時，可能會遇到 CORS（跨來源資源共享）問題，需要後端正確設置 HTTP 標頭。

## 一句總結
`Response` 物件是 Fetch API 的核心組件，負責處理網絡請求的回應數據，並提供多種方法以獲取響應內容。