<!--
Meta Description: # WebTransportDatagramDuplexStream：JavaScript 的新興傳輸技術 ## 概述 WebTransportDatagramDuplexStream 是一個 JavaScript 接口，旨在支持在網頁應用程序中進行高效的雙向數據流傳輸，特別針對低延遲應用而設計。它...
Meta Keywords: transport, datagramstream, webtransportdatagramduplexstream, const, javascript
-->

# WebTransportDatagramDuplexStream：JavaScript 的新興傳輸技術

## 概述
WebTransportDatagramDuplexStream 是一個 JavaScript 接口，旨在支持在網頁應用程序中進行高效的雙向數據流傳輸，特別針對低延遲應用而設計。它基於 WebTransport 協議，提供了方便的 API 來發送和接收數據報文。

## 文檔
### 目的
WebTransportDatagramDuplexStream 使開發者能夠以低延遲的方式在客戶端和服務器之間傳輸數據，這對於遊戲、視訊通話及實時應用特別重要。

### 使用方法
要使用 WebTransportDatagramDuplexStream，開發者需首先創建一個 WebTransport 連接，然後從該連接中獲取 Datagram Duplex Stream。

```javascript
const transport = new WebTransport('wss://example.com');

transport.ready.then(() => {
    const datagramStream = transport.datagramStream;
    // 使用 datagramStream 進行數據傳輸
});
```

### 詳細說明
WebTransportDatagramDuplexStream 提供以下功能：
- **雙向數據流**：支持同時發送和接收數據報文。
- **低延遲**：專為需要即時反應的應用設計，減少數據傳輸延遲。
- **可靠性**：支持流的可靠性設置，開發者可以選擇可靠或不可靠的數據傳輸模式。

### API 方法
- `send(data: ArrayBuffer)`: 發送數據報文。
- `read()`: 讀取接收到的數據報文。

## 範例
以下是使用 WebTransportDatagramDuplexStream 的基本範例：

### 發送數據
```javascript
const transport = new WebTransport('wss://example.com');

transport.ready.then(() => {
    const datagramStream = transport.datagramStream;
    
    const dataToSend = new Uint8Array([1, 2, 3, 4]);
    datagramStream.send(dataToSend.buffer);
});
```

### 接收數據
```javascript
const transport = new WebTransport('wss://example.com');

transport.ready.then(() => {
    const datagramStream = transport.datagramStream;

    async function receiveData() {
        while (true) {
            const { value, done } = await datagramStream.read();
            if (done) break;
            console.log('Received:', new Uint8Array(value));
        }
    }

    receiveData();
});
```

## 解釋
### 常見問題
1. **兼容性問題**：並非所有瀏覽器都支持 WebTransport，請檢查瀏覽器兼容性。
2. **數據丟失**：使用不可靠模式時，數據可能會丟失，需要在應用層進行額外的錯誤處理。

### 額外說明
在使用 WebTransportDatagramDuplexStream 時，建議開發者進行性能測試，以確保其在實際應用中的表現符合需求。

## 一句總結
WebTransportDatagramDuplexStream 是一個強大的 JavaScript 接口，專為低延遲的雙向數據傳輸而設計，適合實時應用。