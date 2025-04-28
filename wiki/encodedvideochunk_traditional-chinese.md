<!--
Meta Description: # EncodedVideoChunk：JavaScript 中的視頻編碼片段 ## 概述 `EncodedVideoChunk` 是一個在 JavaScript 中用於處理視頻編碼的物件，主要用於 Web 平台的媒體處理，特別是在媒體流、視頻編碼和解碼的上下文中。 ## 文檔 ### 目的 `En...
Meta Keywords: encodedvideochunk, javascript, timestamp, const, new
-->

# EncodedVideoChunk：JavaScript 中的視頻編碼片段

## 概述
`EncodedVideoChunk` 是一個在 JavaScript 中用於處理視頻編碼的物件，主要用於 Web 平台的媒體處理，特別是在媒體流、視頻編碼和解碼的上下文中。

## 文檔
### 目的
`EncodedVideoChunk` 物件的主要目的是封裝視頻編碼的信息，讓開發者能夠在處理視頻數據時更加靈活和高效。它通常用於媒體流的編碼和解碼過程中，支持流式數據傳輸和即時視頻處理。

### 使用方法
`EncodedVideoChunk` 的創建通常是由媒體編碼器自動完成，但開發者也可以手動創建以進行特定的視頻處理。

#### 語法
```javascript
const videoChunk = new EncodedVideoChunk({
    type: 'key', // 或 'delta'
    timestamp: 123456789, // 時間戳
    data: new Uint8Array([...]) // 二進制數據
});
```

### 詳細說明
- **type**：指示視頻片段的類型。可以是 `'key'`（關鍵幀）或 `'delta'`（增量幀）。
- **timestamp**：表示該片段的時間戳，以毫秒為單位。
- **data**：一個 `Uint8Array`，包含編碼後的視頻數據。

此物件主要用於與 `VideoEncoder` 和 `VideoDecoder` API 互動，以便於視頻的實時編碼和解碼。

## 範例
### 基本用法
下面是一個簡單的範例，演示如何創建一個 `EncodedVideoChunk` 物件：

```javascript
const timestamp = Date.now(); // 獲取當前時間戳
const videoData = new Uint8Array([/* 編碼後的視頻數據 */]);

const videoChunk = new EncodedVideoChunk({
    type: 'key', // 這是一個關鍵幀
    timestamp: timestamp,
    data: videoData
});

console.log(videoChunk);
```

## 解釋
### 常見陷阱
1. **時間戳不一致**：確保時間戳是正確的，否則可能導致視頻播放不同步。
2. **數據格式**：`data` 必須是 `Uint8Array` 格式，否則將無法正確處理。
3. **片段類型**：確保根據視頻編碼的需求選擇正確的片段類型（關鍵幀或增量幀），以避免解碼問題。

### 額外說明
在使用 `EncodedVideoChunk` 時，建議對其與 `VideoEncoder` 和 `VideoDecoder` 進行充分的了解，以便有效管理視頻流的編碼和解碼過程。此外，考慮瀏覽器的兼容性，因為某些 API 可能在不同的環境中表現不一。

## 一句總結
`EncodedVideoChunk` 是 JavaScript 中用於封裝視頻編碼數據的物件，對於實現實時視頻處理至關重要。