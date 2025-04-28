<!--
Meta Description: # JavaScript MediaRecorder API 使用指南 ## 摘要 MediaRecorder 是一個 JavaScript API，允許開發者錄製媒體流（音頻及視頻），並將其保存為檔案格式，方便後續使用或上傳。 ## 文檔 ### 目的 MediaRecorder API 旨在提供...
Meta Keywords: mediarecorder, javascript, function, const, blob
-->

# JavaScript MediaRecorder API 使用指南

## 摘要
MediaRecorder 是一個 JavaScript API，允許開發者錄製媒體流（音頻及視頻），並將其保存為檔案格式，方便後續使用或上傳。

## 文檔
### 目的
MediaRecorder API 旨在提供一個簡單的介面來錄製媒體流，並支援多種格式，讓開發者能夠輕鬆捕捉音視頻內容，應用於網頁應用程式中。

### 使用方法
要使用 MediaRecorder，首先需要獲取一個媒體流（通常通過 `getUserMedia` 方法），然後創建一個 MediaRecorder 實例。以下是基本的使用步驟：

1. 獲取媒體流：
   ```javascript
   navigator.mediaDevices.getUserMedia({ audio: true, video: true })
       .then(function(stream) {
           // 使用獲取的媒體流
       })
       .catch(function(error) {
           console.error("獲取媒體流失敗:", error);
       });
   ```

2. 創建 MediaRecorder 實例：
   ```javascript
   const mediaRecorder = new MediaRecorder(stream);
   ```

3. 開始錄製：
   ```javascript
   mediaRecorder.start();
   ```

4. 停止錄製：
   ```javascript
   mediaRecorder.stop();
   ```

5. 處理錄製結果：
   ```javascript
   mediaRecorder.ondataavailable = function(event) {
       if (event.data.size > 0) {
           const blob = new Blob([event.data], { type: 'video/webm' });
           const url = URL.createObjectURL(blob);
           // 可以將 blob 上傳或顯示
       }
   };
   ```

### 詳細說明
MediaRecorder API 提供了多個事件和方法，如下：

- `start()`: 開始錄製媒體流。
- `stop()`: 停止錄製媒體流。
- `pause()`: 暫停錄製。
- `resume()`: 恢復錄製。
- `ondataavailable`: 當錄製的數據可用時觸發，通常用於獲取錄製的媒體數據。
- `onerror`: 當發生錯誤時觸發。

## 範例
### 基本範例
以下是錄音的基本範例：

```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(function(stream) {
        const mediaRecorder = new MediaRecorder(stream);
        
        let chunks = [];
        
        mediaRecorder.ondataavailable = function(event) {
            chunks.push(event.data);
        };

        mediaRecorder.onstop = function() {
            const blob = new Blob(chunks, { type: 'audio/webm' });
            const url = URL.createObjectURL(blob);
            const audio = new Audio(url);
            audio.play();
        };

        mediaRecorder.start();

        // 停止錄製於3秒後
        setTimeout(() => {
            mediaRecorder.stop();
        }, 3000);
    })
    .catch(function(error) {
        console.error("獲取媒體流失敗:", error);
    });
```

## 解釋
在使用 MediaRecorder 時，有幾個常見的注意事項：

1. **瀏覽器相容性**: MediaRecorder API 在某些瀏覽器中可能不完全支援，確保查閱最新的相容性資訊。
2. **格式問題**: 錄製的媒體格式取決於瀏覽器及其支援的編碼格式，使用 `mimeType` 參數來指定所需格式。
3. **異步行為**: 操作如 `getUserMedia` 和 `ondataavailable` 是異步的，必須適當處理這些異步行為以避免錯誤。

## 一句總結
MediaRecorder API 是一個強大而方便的工具，讓開發者可以輕鬆錄製音視頻媒體流，並將其保存為檔案。