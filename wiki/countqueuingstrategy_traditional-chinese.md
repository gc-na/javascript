<!--
Meta Description: # CountQueuingStrategy：JavaScript 中的計數排隊策略 ## 簡介 `CountQueuingStrategy` 是 JavaScript 中的一種排隊策略，用於控制流的壓力和吞吐量，主要應用於可讀流（Readable Streams）和可寫流（Writable Str...
Meta Keywords: countqueuingstrategy, javascript, const, writablestream, new
-->

# CountQueuingStrategy：JavaScript 中的計數排隊策略

## 簡介
`CountQueuingStrategy` 是 JavaScript 中的一種排隊策略，用於控制流的壓力和吞吐量，主要應用於可讀流（Readable Streams）和可寫流（Writable Streams）中。它根據排隊中的數據項目數量來決定何時進行流的讀取和寫入。

## 文檔
### 目的
`CountQueuingStrategy` 的主要目的是讓開發者可以根據排隊中的數據項目數量來管理流的行為。這有助於優化數據流的處理效率，特別是在處理大量數據時。

### 用法
要使用 `CountQueuingStrategy`，首先需要創建一個新的實例，然後將其作為選項傳遞給可讀流或可寫流的構造函數。以下是創建 `CountQueuingStrategy` 的基本語法：

```javascript
const strategy = new CountQueuingStrategy({
  highWaterMark: 16 // 設定高水位標記
});
```

這裡的 `highWaterMark` 參數定義了隊列中可以容納的最大項目數量。當隊列中的項目數量達到這個值，流將會停止接收新的數據，直到有足夠的空間可以接受新的項目。

## 範例
以下是使用 `CountQueuingStrategy` 的基本範例：

### 範例 1：創建可寫流
```javascript
const { WritableStream } = require('stream/web');

const writableStream = new WritableStream({
  write(chunk) {
    console.log(`寫入數據：${chunk}`);
  }
}, new CountQueuingStrategy({ highWaterMark: 2 }));

writableStream.write('數據1');
writableStream.write('數據2');
writableStream.write('數據3'); // 此時流會阻塞，等待空間
```

### 範例 2：創建可讀流
```javascript
const { ReadableStream } = require('stream/web');

const readableStream = new ReadableStream({
  pull(controller) {
    controller.enqueue('數據項');
  }
}, new CountQueuingStrategy({ highWaterMark: 5 }));

const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  console.log(`讀取數據：${value}`);
});
```

## 解釋
使用 `CountQueuingStrategy` 時，開發者需要注意以下幾點：

- **高水位標記**：適當設置 `highWaterMark` 的值非常重要，過低的值可能導致流的頻繁阻塞，而過高的值則可能導致內存使用過高。
- **流的狀態管理**：開發者需要管理流的狀態，以確保數據的正確讀寫。特別是在異步操作中，需謹慎處理流的暫停與恢復。
- **性能考量**：在高頻率數據流中，對 `CountQueuingStrategy` 的使用可以顯著提高性能，但也須根據應用場景進行調整與測試。

## 一句總結
`CountQueuingStrategy` 是一種基於數據項目數量的流控制策略，有助於優化 JavaScript 中的可讀和可寫流的性能。