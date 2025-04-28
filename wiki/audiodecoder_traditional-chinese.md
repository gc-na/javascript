<!--
Meta Description: # AudioDecoder: JavaScript 中的音訊解碼器 ## 概要 `AudioDecoder` 是一個 Web API，允許開發者在 JavaScript 中解碼音頻數據，從而進行即時處理和播放。這個 API 特別適用於需要低延遲音頻解碼的應用，例如實時通訊和音頻編輯工具。 ## 文...
Meta Keywords: audiodecoder, javascript, output, error, decoder
-->

# AudioDecoder: JavaScript 中的音訊解碼器

## 概要
`AudioDecoder` 是一個 Web API，允許開發者在 JavaScript 中解碼音頻數據，從而進行即時處理和播放。這個 API 特別適用於需要低延遲音頻解碼的應用，例如實時通訊和音頻編輯工具。

## 文檔

### 目的
`AudioDecoder` 的主要目的是提供一種高效的方式來解碼音頻數據，支持多種音頻格式。這個 API 使開發者能夠在網頁應用中實現更流暢的音頻體驗，並減少解碼過程中的延遲。

### 使用方法
要使用 `AudioDecoder`，開發者需要先創建一個解碼器實例，然後提供必要的配置，包括音頻格式和解碼回調函數。以下是使用 `AudioDecoder` 的基本步驟：

1. **創建解碼器實例**：
   ```javascript
   const decoder = new AudioDecoder({
       output: handleOutput,  // 解碼完的音頻回調函數
       error: handleError     // 錯誤處理函數
   });
   ```

2. **解碼音頻數據**：
   使用 `decode()` 方法將音頻數據解碼：
   ```javascript
   decoder.decode(encodedAudioData);
   ```

3. **處理解碼結果**：
   在 `output` 回調中，處理解碼後的音頻緩衝區。

### 參數
- **output**: 一個函數，當解碼完成後會被調用，並傳入解碼後的音頻數據。
- **error**: 一個函數，用於處理解碼過程中出現的任何錯誤。

## 範例

### 基本使用範例
以下是一個簡單的示例，展示如何使用 `AudioDecoder` 來解碼音頻數據：

```javascript
const decoder = new AudioDecoder({
    output: (audioData) => {
        // 將解碼後的音頻數據傳遞到音頻上下文進行播放
        audioContext.decodeAudioData(audioData, (buffer) => {
            const source = audioContext.createBufferSource();
            source.buffer = buffer;
            source.connect(audioContext.destination);
            source.start();
        });
    },
    error: (e) => {
        console.error('解碼錯誤:', e);
    }
});

// 假設 encodedAudioData 是一段已編碼的音頻數據
decoder.decode(encodedAudioData);
```

## 解釋
使用 `AudioDecoder` 時，開發者需注意以下幾點：

1. **格式支持**: 確保所使用的音頻格式是被 `AudioDecoder` 支持的，否則可能會導致錯誤。
2. **回調函數**: 適當處理 `output` 和 `error` 回調，以避免在解碼過程中出現未處理的異常。
3. **性能考量**: 在大量音頻數據解碼時，應考慮性能問題，並適當限制同時運行的解碼器數量。

## 總結
`AudioDecoder` 是一個強大的工具，能夠在 JavaScript 中高效地解碼音頻數據，為音頻應用提供低延遲的性能。