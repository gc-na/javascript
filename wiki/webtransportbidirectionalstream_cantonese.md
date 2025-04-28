<!--
Meta Description: # WebTransportBidirectionalStream：JavaScript 中的全雙工流傳輸 ## 概述 WebTransportBidirectionalStream 是一個用於在 WebTransport 連接中實現全雙工數據流的 JavaScript 介面，旨在提供低延遲數據傳輸...
Meta Keywords: webtransportbidirectionalstream, webtransport, const, javascript, transport
-->

# WebTransportBidirectionalStream：JavaScript 中的全雙工流傳輸

## 概述
WebTransportBidirectionalStream 是一個用於在 WebTransport 連接中實現全雙工數據流的 JavaScript 介面，旨在提供低延遲數據傳輸，特別適用於即時通訊和流媒體應用。

## 文檔
### 目的
WebTransportBidirectionalStream 允許開發者在一個 WebTransport 連接中同時發送和接收數據。這意味著數據可以在客戶端和服務器之間雙向流動，而不需要建立多個連接。

### 用法
當您使用 WebTransport API 時，可以使用 WebTransportBidirectionalStream 來創建一個雙向流。這個流可以用來發送和接收消息，並且支持流控制和數據分段。

#### 主要屬性和方法
- `readable`: 返回一個可讀流，允許從流中讀取數據。
- `writable`: 返回一個可寫流，允許向流中寫入數據。
- `close()`: 關閉流並結束傳輸。

### 詳細信息
WebTransportBidirectionalStream 是 WebTransport 的一部分，該 API 提供一種新的方式來傳輸數據，特別是針對需要即時數據傳送的應用。WebTransportBidirectionalStream 的實現基於 QUIC 協議，這使得其在性能上具有優勢。

## 示例
以下是使用 WebTransportBidirectionalStream 的基本示例：

```javascript
async function startTransport() {
    const transport = new WebTransport('https://example.com/transport');

    await transport.ready;

    const stream = await transport.openBidirectionalStream();

    const writer = stream.writable.getWriter();
    const reader = stream.readable.getReader();

    // 寫入數據
    await writer.write(new TextEncoder().encode('Hello, Server!'));

    // 讀取數據
    const { done, value } = await reader.read();
    if (!done) {
        console.log(new TextDecoder().decode(value));
    }

    writer.releaseLock();
    reader.releaseLock();
    stream.close();
}
startTransport();
```

## 解釋
在使用 WebTransportBidirectionalStream 時，開發者需注意以下幾個常見問題：
- **連接狀態**：在嘗試開啟流之前，必須確保 WebTransport 連接已經準備好。
- **流控制**：請注意流的可讀性和可寫性，以避免數據丟失或錯誤。
- **錯誤處理**：始終實施錯誤處理機制，以應對可能的連接問題或數據傳輸錯誤。

## 一句話總結
WebTransportBidirectionalStream 是一個強大的 JavaScript 接口，旨在通過全雙工流提高 Web 應用的數據傳輸效率。