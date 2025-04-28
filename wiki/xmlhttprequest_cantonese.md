<!--
Meta Description: # XMLHttpRequest 在 JavaScript 的使用及詳情 ## 概述 `XMLHttpRequest` 係一個 JavaScript 物件，主要用於同伺服器進行非同步請求，常見於 AJAX 技術中，幫助開發者實現無需重新載入網頁就能獲取資料。 ## 文件說明 `XMLHttpRequ...
Meta Keywords: xhr, xmlhttprequest, javascript, open, get
-->

# XMLHttpRequest 在 JavaScript 的使用及詳情

## 概述
`XMLHttpRequest` 係一個 JavaScript 物件，主要用於同伺服器進行非同步請求，常見於 AJAX 技術中，幫助開發者實現無需重新載入網頁就能獲取資料。

## 文件說明
`XMLHttpRequest` 物件可以用來發送 HTTP 請求同接收伺服器的回應，通常用於網頁應用程式中嘅資料傳輸。佢支持 GET 和 POST 請求，並且可以處理各種格式的回應數據，包括 JSON、XML 和純文本。

### 用法
1. **創建 XMLHttpRequest 物件**：
   ```javascript
   var xhr = new XMLHttpRequest();
   ```

2. **配置請求**：
   使用 `open` 方法設置請求類型及 URL：
   ```javascript
   xhr.open('GET', 'https://api.example.com/data', true);
   ```

3. **設置回調函數**：
   當請求完成時，需設置 `onreadystatechange` 事件來處理回應：
   ```javascript
   xhr.onreadystatechange = function() {
       if (xhr.readyState === 4 && xhr.status === 200) {
           console.log(xhr.responseText);
       }
   };
   ```

4. **發送請求**：
   使用 `send` 方法發送請求：
   ```javascript
   xhr.send();
   ```

## 示例
### 基本 GET 請求示例
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(JSON.parse(xhr.responseText));
    }
};
xhr.send();
```

### 基本 POST 請求示例
```javascript
var xhr = new XMLHttpRequest();
xhr.open('POST', 'https://api.example.com/submit', true);
xhr.setRequestHeader('Content-Type', 'application/json;charset=UTF-8');
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send(JSON.stringify({ name: 'John', age: 30 }));
```

## 解釋
- **常見錯誤**：開發者經常忽略檢查 `readyState` 和 `status`，這可能導致無法正確處理回應。
- **跨域請求**：使用 `XMLHttpRequest` 進行跨域請求時，可能會遇到 CORS（跨來源資源共享）問題，需確保伺服器已正確設置 CORS 標頭。
- **同步請求**：雖然可以使用同步模式（將 `open` 方法的第三個參數設置為 `false`），但這樣會阻塞主執行緒，影響用戶體驗，因此不建議使用。

## 一句總結
`XMLHttpRequest` 係一個強大的工具，讓開發者可以輕鬆地進行非同步 HTTP 請求，從而提升網頁應用程式的互動性。