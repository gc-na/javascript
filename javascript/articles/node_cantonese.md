<!--
Meta Description: # Node.js：JavaScript 的伺服器端運行環境 ## 簡介 Node.js 是一個開源的伺服器端運行環境，基於 Google 的 V8 JavaScript 引擎，允許開發者使用 JavaScript 來編寫伺服器端的應用程式。 ## 文檔 Node.js 的主要目的是提供一個非阻塞、...
Meta Keywords: node, javascript, http, const, res
-->

# Node.js：JavaScript 的伺服器端運行環境

## 簡介
Node.js 是一個開源的伺服器端運行環境，基於 Google 的 V8 JavaScript 引擎，允許開發者使用 JavaScript 來編寫伺服器端的應用程式。

## 文檔
Node.js 的主要目的是提供一個非阻塞、事件驅動的環境，適合開發高效能的網絡應用程式。它的架構使得處理大量並發連線變得更加容易，並且對於 I/O 密集型的應用程式特別有效。

### 使用
Node.js 可以用來創建各種網絡應用程式，包括但不限於：
- RESTful API
- 網站後端服務
- 實時應用程式（如聊天應用和遊戲）

要開始使用 Node.js，首先需要在你的系統上安裝 Node.js。安裝完成後，你可以通過命令行使用 `node` 命令來執行 JavaScript 檔案。

### 安裝 Node.js
1. 訪問 Node.js 的官方網站 [nodejs.org](https://nodejs.org)。
2. 根據你的操作系統下載適合的安裝包。
3. 按照安裝指示完成安裝。

## 示例
以下是一個簡單的 Node.js 程式，演示如何建立一個基本的 HTTP 伺服器：

```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`伺服器運行於 http://${hostname}:${port}/`);
});
```

執行這段程式後，你可以通過瀏覽器訪問 `http://127.0.0.1:3000` 來查看 "Hello World" 信息。

## 解釋
在使用 Node.js 時，有些常見的陷阱和注意事項包括：
- **非阻塞 I/O**：Node.js 使用非阻塞的方式處理 I/O 操作，這要求開發者理解事件驅動的編程模型。
- **單執行緒**：儘管 Node.js 可以處理大量的並發請求，但它是單執行緒的，這意味著如果有長時間運行的運算，會影響到伺服器的性能。
- **模塊管理**：Node.js 有一個強大的模塊系統（CommonJS），使用 `require` 來導入模塊，但需注意模塊的依賴關係。

## 一句總結
Node.js 是一個基於事件驅動和非阻塞 I/O 的伺服器端 JavaScript 環境，適合開發高效能的網絡應用程式。