<!--
Meta Description: # Node.js：JavaScript的伺服器端執行環境 ## 概要 Node.js是一個開源的跨平台JavaScript執行環境，基於Chrome的V8引擎構建，旨在為伺服器端的應用程式提供非同步事件驅動的架構。 ## 文檔 Node.js的主要目的是使JavaScript能夠在伺服器上運行，從...
Meta Keywords: node, http, res, const, server
-->

# Node.js：JavaScript的伺服器端執行環境

## 概要
Node.js是一個開源的跨平台JavaScript執行環境，基於Chrome的V8引擎構建，旨在為伺服器端的應用程式提供非同步事件驅動的架構。

## 文檔
Node.js的主要目的是使JavaScript能夠在伺服器上運行，從而擴展JavaScript的應用範圍。開發者可以使用Node.js來建立網絡應用程式，API服務，甚至是全功能的伺服器。Node.js擁有強大的包管理工具npm，使得安裝和管理依賴變得簡單。

### 主要特性
- **非同步I/O**：Node.js使用事件驅動模型，能夠高效處理大量的並發連接。
- **單執行緒**：雖然Node.js是單執行緒的，但它可以通過非同步處理來避免阻塞。
- **npm**：Node.js的包管理系統，提供了超過一百萬個開源庫。

### 使用方法
要使用Node.js，首先需要在系統上安裝它。安裝完成後，可以通過命令行執行JavaScript檔案，如下所示：
```bash
node yourfile.js
```

## 範例
以下是一個簡單的Node.js伺服器範例：
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}/`);
});
```
這段程式碼創建了一個簡單的HTTP伺服器，當用戶訪問時會返回“Hello, World!”的訊息。

## 解釋
在使用Node.js時，開發者需注意以下常見問題：
- **回呼地獄**：由於Node.js是非同步的，可能會導致代碼結構複雜。使用Promises或async/await可以改善代碼可讀性。
- **單執行緒限制**：雖然Node.js適合I/O密集型任務，但對於CPU密集型任務可能會造成性能瓶頸。
- **錯誤處理**：在非同步編程中，錯誤處理尤為重要，開發者必須確保正確捕獲和處理錯誤。

## 總結
Node.js是一個強大的JavaScript執行環境，適合用於開發高效能的伺服器端應用程式。