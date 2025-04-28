<!--
Meta Description: # XMLHttpRequest：JavaScript 的網路請求接口 ## 摘要 `XMLHttpRequest` 是一個 JavaScript 物件，用於在網頁中與伺服器進行非同步請求。它使得開發者能夠從伺服器獲取資料，並在不重新加載整個頁面的情況下更新部分網頁內容。 ## 文檔 ### 目的 ...
Meta Keywords: xhr, xmlhttprequest, javascript, post, onreadystatechange
-->

# XMLHttpRequest：JavaScript 的網路請求接口

## 摘要
`XMLHttpRequest` 是一個 JavaScript 物件，用於在網頁中與伺服器進行非同步請求。它使得開發者能夠從伺服器獲取資料，並在不重新加載整個頁面的情況下更新部分網頁內容。

## 文檔
### 目的
`XMLHttpRequest` 主要用於在網頁應用程式中進行非同步資料請求，允許開發者從伺服器獲取數據或發送數據。

### 用法
1. **創建一個 XMLHttpRequest 物件**
   ```javascript
   var xhr = new XMLHttpRequest();
   ```

2. **配置請求**
   ```javascript
   xhr.open(method, url, async);
   ```
   - `method`：HTTP 方法（如 "GET", "POST"）。
   - `url`：請求的 URL。
   - `async`：是否使用非同步請求，預設為 `true`。

3. **設置回調函數**
   ```javascript
   xhr.onreadystatechange = function() {
       if (xhr.readyState === 4 && xhr.status === 200) {
           console.log(xhr.responseText);
       }
   };
   ```

4. **發送請求**
   ```javascript
   xhr.send(data);
   ```
   - `data`：可選，發送的數據（僅對 "POST" 方法有效）。

### 詳細信息
- `readyState`：表示請求的當前狀態，範圍從 0 到 4。
  - 0: 尚未初始化
  - 1: 請求已建立
  - 2: 請求已發送
  - 3: 請求處理中
  - 4: 請求已完成

- `status`：HTTP 狀態碼，例如 200 表示成功，404 表示未找到。

- `responseText`：伺服器回應的文本內容。

## 範例
### 基本的 GET 請求
```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### 基本的 POST 請求
```javascript
var xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/data", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send(JSON.stringify({ key: "value" }));
```

## 說明
- **常見陷阱**：請確保在發送請求之前已正確設置 `onreadystatechange` 回調，否則可能會導致無法獲取回應數據。
- **跨域請求**：使用 `XMLHttpRequest` 時，請注意同源政策（Same Origin Policy），這可能會影響到從不同網域請求資源的能力。
- **非同步請求**：若使用非同步請求，確保在回調中處理資料更新，以避免在請求完成之前嘗試使用返回的數據。

## 一句總結
`XMLHttpRequest` 是一個強大的 JavaScript 物件，用於實現非同步網路請求，從而提升網頁應用程式的互動性和響應速度。