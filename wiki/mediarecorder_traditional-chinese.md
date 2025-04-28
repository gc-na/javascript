<!--
Meta Description: # MediaRecorder：JavaScript 中的媒體錄製 API ## 簡介 MediaRecorder 是一個強大的 API，允許開發者在網頁應用程式中錄製音頻和視頻。它利用瀏覽器的媒體捕捉能力，提供了一個簡單的介面來創建媒體流的錄製。 ## 文檔 ### 目的 MediaRecorde...
Meta Keywords: mediarecorder, api, audio, function, const
-->

# MediaRecorder：JavaScript 中的媒體錄製 API

## 簡介
MediaRecorder 是一個強大的 API，允許開發者在網頁應用程式中錄製音頻和視頻。它利用瀏覽器的媒體捕捉能力，提供了一個簡單的介面來創建媒體流的錄製。

## 文檔
### 目的
MediaRecorder API 主要用於錄製媒體流（如從使用者的攝像頭或麥克風獲得的音頻和視頻）。它可以用於創建應用程式，例如視頻聊天、錄音應用或任何需要捕捉媒體內容的功能。

### 使用方法
要使用 MediaRecorder，開發者需要首先獲取一個媒體流，通常是通過 `getUserMedia()` 方法。然後，可以創建一個 MediaRecorder 實例，並開始錄製。

### 主要屬性和方法
- **constructor**：MediaRecorder(mediaStream) - 創建一個新的 MediaRecorder 實例。
- **start([timeslice])**：開始錄製媒體流，`timeslice` 參數可選，指定每次錄製的時間片（以毫秒為單位）。
- **stop()**：停止錄製。
- **requestData()**：請求當前的錄製數據。
- **ondataavailable**：當有錄製數據可用時觸發的事件。
- **onerror**：當錄製過程中發生錯誤時觸發的事件。

## 範例
以下是一個簡單的範例，展示如何使用 MediaRecorder 來錄製音頻：

```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(function(mediaStream) {
        const mediaRecorder = new MediaRecorder(mediaStream);
        let audioChunks = [];

        mediaRecorder.ondataavailable = function(event) {
            audioChunks.push(event.data);
        }

        mediaRecorder.onstop = function() {
            const audioBlob = new Blob(audioChunks, { type: 'audio/wav' });
            const audioUrl = URL.createObjectURL(audioBlob);
            const audio = new Audio(audioUrl);
            audio.play();
        }

        mediaRecorder.start();

        // 停止錄製 3 秒後
        setTimeout(function() {
            mediaRecorder.stop();
        }, 3000);
    })
    .catch(function(err) {
        console.error("獲取媒體流失敗:", err);
    });
```

## 解釋
### 常見陷阱和注意事項
1. **瀏覽器支持**：MediaRecorder API 的支持情況因瀏覽器而異，確保在使用之前檢查瀏覽器的兼容性。
2. **HTTP 和 HTTPS**：某些瀏覽器要求在安全上下文（HTTPS）中使用 `getUserMedia()` 方法，因此確保你的網站使用 HTTPS。
3. **錄製格式**：錄製的數據格式取決於瀏覽器及其支持的編碼器。使用 `MediaRecorder.isTypeSupported(mimeType)` 方法來檢查所需格式的支持情況。
4. **數據可用性**：在錄製過程中，`ondataavailable` 事件可能不會每次都觸發，這取決於錄製設定和媒體流的特性。

## 一句話總結
MediaRecorder API 是一個簡單的介面，允許開發者錄製音頻和視頻流，並在網頁應用中使用。