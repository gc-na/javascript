<!--
Meta Description: # WebTransportBidirectionalStream 在 JavaScript 中的應用與使用 ## 概述 WebTransportBidirectionalStream 是一種用於 WebTransport 的 API，允許在客戶端和伺服器之間進行雙向通信，適用於需要高效傳輸的應用程...
Meta Keywords: webtransportbidirectionalstream, webtransport, new, const, transport
-->

# WebTransportBidirectionalStream 在 JavaScript 中的應用與使用

## 概述
WebTransportBidirectionalStream 是一種用於 WebTransport 的 API，允許在客戶端和伺服器之間進行雙向通信，適用於需要高效傳輸的應用程式，如即時通訊和遊戲。

## 文檔
WebTransportBidirectionalStream 提供了一個流的接口，使開發者能夠在單個連接上同時發送和接收數據。此 API 是為了解決基於 HTTP 的傳輸協議在低延遲和高頻率數據傳輸上的限制而設計的。

### 目的
WebTransportBidirectionalStream 的主要目的是提高網頁應用的數據傳輸效率，特別是對於需要頻繁的資料交換的情境。

### 使用
要使用 WebTransportBidirectionalStream，開發者需要首先建立一個 WebTransport 連接，然後可以通過該連接獲取一個 BidirectionalStream 來進行數據的發送與接收。

### 詳細說明
- **創建 WebTransport 連接**：使用 `new WebTransport(url)` 來創建一個連接。
- **獲取流**：連接成功後，可以調用 `createBidirectionalStream()` 方法來獲取雙向流。
- **數據的發送與接收**：利用 `WritableStream` 和 `ReadableStream` 進行數據的寫入和讀取。

## 範例
以下是 WebTransportBidirectionalStream 的基本用法範例：

```javascript
const transport = new WebTransport('wss://example.com/transport');

transport.ready
  .then(() => {
    const stream = transport.createBidirectionalStream();

    const writer = stream.writable.getWriter();
    writer.write(new TextEncoder().encode('Hello, Server!'));
    writer.close();

    const reader = stream.readable.getReader();
    reader.read().then(({ done, value }) => {
      if (!done) {
        console.log(new TextDecoder().decode(value));
      }
    });
  })
  .catch((error) => {
    console.error('連接失敗:', error);
  });
```

## 解釋
在使用 WebTransportBidirectionalStream 時，有幾個常見的陷阱和注意事項：
- **連接狀態**：確保在創建流之前，WebTransport 連接已成功建立。
- **流的關閉**：在完成數據傳輸後，記得關閉流，以釋放資源。
- **錯誤處理**：對於數據傳輸過程中的錯誤，應進行適當的處理，以提高應用的穩定性。

## 一句總結
WebTransportBidirectionalStream 提供了一種高效的雙向數據傳輸方式，適合用於需要即時通訊的網頁應用。