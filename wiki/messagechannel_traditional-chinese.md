<!--
Meta Description: # JavaScript 中的 MessageChannel：跨執行緒通訊的利器 ## 概述 MessageChannel 是一種 Web API，允許在不同執行緒之間進行高效的訊息傳遞。這對於 Web Worker 和主執行緒之間的非同步通訊非常有用。 ## 文件說明 MessageChannel...
Meta Keywords: messagechannel, worker, port1, channel, event
-->

# JavaScript 中的 MessageChannel：跨執行緒通訊的利器

## 概述
MessageChannel 是一種 Web API，允許在不同執行緒之間進行高效的訊息傳遞。這對於 Web Worker 和主執行緒之間的非同步通訊非常有用。

## 文件說明
MessageChannel 提供了一種簡單的方式來創建一對通道，這些通道可以用於在不同的執行緒之間發送訊息。每個 MessageChannel 物件都有兩個端口（port1 和 port2），這些端口可用於發送和接收訊息。

### 主要用途
- **非同步通訊**：在 Web Worker 與主執行緒之間傳遞資料。
- **解耦**：將不同執行緒的任務解耦，使其可以獨立運行。

### 使用方式
1. 創建一個 MessageChannel 實例：
   ```javascript
   const channel = new MessageChannel();
   ```

2. 使用 port1 發送訊息：
   ```javascript
   channel.port1.postMessage('Hello from port1!');
   ```

3. 在 port2 上接收訊息：
   ```javascript
   channel.port2.onmessage = (event) => {
       console.log(event.data); // 輸出：Hello from port1!
   };
   ```

## 範例
### 基本用法
以下是一個簡單的示例，展示如何使用 MessageChannel 在主執行緒與 Web Worker 之間傳遞訊息：

```javascript
// 主執行緒
const worker = new Worker('worker.js');
const channel = new MessageChannel();

worker.postMessage({ port: channel.port1 }, [channel.port1]);

channel.port2.onmessage = (event) => {
    console.log("主執行緒收到訊息:", event.data);
};

// worker.js
onmessage = function(event) {
    const port = event.data.port;
    port.postMessage("來自 Worker 的訊息");
};
```

## 解釋
### 常見陷阱與注意事項
- **端口的傳遞**：當通過 postMessage 傳遞端口時，必須使用 `transfer` 參數，否則端口將無法正常使用。
- **一次性端口**：每個端口只能使用一次，發送後會被關閉，無法再次使用。
- **資料類型**：MessageChannel 支持序列化的資料類型，對於非可序列化的資料（如函數）需特別注意。

## 總結
MessageChannel 是一個強大的工具，提供了在不同執行緒之間輕鬆進行非同步通訊的能力，適合用於 Web 應用中的高效能任務處理。