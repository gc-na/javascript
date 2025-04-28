<!--
Meta Description: # JavaScript Response 物件詳細介紹 ## 概述 在 JavaScript 中，`Response` 物件是 Fetch API 的一部分，用於表示 HTTP 請求的回應。它包含了來自伺服器的數據，並提供一系列方法來處理這些數據。 ## 文檔 `Response` 物件的主要目的...
Meta Keywords: response, fetch, api, then, javascript
-->

# JavaScript Response 物件詳細介紹

## 概述
在 JavaScript 中，`Response` 物件是 Fetch API 的一部分，用於表示 HTTP 請求的回應。它包含了來自伺服器的數據，並提供一系列方法來處理這些數據。

## 文檔
`Response` 物件的主要目的是為了處理從伺服器返回的資料。當我們使用 Fetch API 發送請求後，會返回一個 `Response` 物件，此物件包含了以下屬性和方法：

- **屬性**:
  - `status`: HTTP 狀態碼（如 200、404 等）
  - `statusText`: 與狀態碼對應的訊息
  - `headers`: 包含回應標頭的 `Headers` 物件
  - `url`: 請求的 URL
  - `ok`: 一個布林值，表示請求是否成功（狀態碼範圍為 200-299）

- **方法**:
  - `json()`: 解析回應的 JSON 數據
  - `text()`: 以文字格式解析回應
  - `blob()`: 以 Blob 格式解析回應
  - `formData()`: 以 FormData 解析回應
  - `arrayBuffer()`: 以 ArrayBuffer 解析回應

### 使用方法
要使用 `Response` 物件，首先需要發送一個 HTTP 請求。以下是使用 Fetch API 獲取數據的範例：

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('There was a problem with the fetch operation:', error);
  });
```

## 範例
以下是幾個使用 `Response` 物件的簡單範例：

1. **獲取 JSON 數據**:

```javascript
fetch('https://api.example.com/users')
  .then(response => response.json())
  .then(users => console.log(users));
```

2. **獲取純文字**:

```javascript
fetch('https://api.example.com/text')
  .then(response => response.text())
  .then(text => console.log(text));
```

3. **獲取 Blob 數據**:

```javascript
fetch('https://api.example.com/image')
  .then(response => response.blob())
  .then(blob => {
    const img = document.createElement('img');
    img.src = URL.createObjectURL(blob);
    document.body.appendChild(img);
  });
```

## 解釋
使用 `Response` 物件時，常見的問題包括：
- **狀態碼檢查**: 忘記檢查 `response.ok` 會導致錯誤處理不當。
- **異步處理**: 確保在 `.then()` 內部處理解析數據，避免在 `fetch` 完成前使用未定義的數據。
- **跨域請求**: 某些 API 可能會因 CORS 設定而無法成功響應，需注意伺服器的設置。

## 一句總結
`Response` 物件是 Fetch API 的核心組件，用於處理和解析 HTTP 請求的回應數據。