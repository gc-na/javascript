<!--
Meta Description: # JavaScript 中的 "onprogress" 事件：理解和應用 ## 簡介 `onprogress` 事件在 JavaScript 中主要用於監控數據加載的進度，特別是在使用 XMLHttpRequest 進行 AJAX 請求或在 Fetch API 中。它提供了一種方法，以便在數據下載...
Meta Keywords: xhr, event, onprogress, let, console
-->

# JavaScript 中的 "onprogress" 事件：理解和應用

## 簡介
`onprogress` 事件在 JavaScript 中主要用於監控數據加載的進度，特別是在使用 XMLHttpRequest 進行 AJAX 請求或在 Fetch API 中。它提供了一種方法，以便在數據下載或上傳的過程中，能夠即時獲取進度信息，從而改善用戶體驗。

## 文檔
### 目的
`onprogress` 事件的主要目的是實時更新數據傳輸的進度，這對於處理大型文件上傳或下載時尤為重要。當用戶需要等待數據加載時，顯示進度條可以增加用戶的滿意度。

### 用法
`onprogress` 事件通常與 XMLHttpRequest 或 Fetch API 一起使用。當發生進度變化時，會觸發此事件，並提供一個事件對象，該對象包含了加載的進度信息。

#### 事件對象
事件對象的屬性包含：
- `loaded`: 已加載的字節數。
- `total`: 總字節數。如果無法確定總字節數，則為 `undefined`。

### 事件綁定
通過以下方式綁定 `onprogress` 事件：
```javascript
let xhr = new XMLHttpRequest();
xhr.open('GET', 'your_file_url', true);
xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        let percentComplete = (event.loaded / event.total) * 100;
        console.log(`加載進度: ${percentComplete}%`);
    } else {
        console.log('無法計算加載進度');
    }
};
xhr.send();
```

## 範例
### 示例 1：基本的進度監控
```javascript
let xhr = new XMLHttpRequest();
xhr.open('GET', 'large_file.zip', true);
xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        let percentComplete = (event.loaded / event.total) * 100;
        console.log(`加載進度: ${percentComplete.toFixed(2)}%`);
    } else {
        console.log('加載進度無法計算');
    }
};
xhr.onload = function() {
    console.log('文件已成功加載');
};
xhr.send();
```

### 示例 2：文件上傳進度
```javascript
let formData = new FormData();
formData.append('file', fileInput.files[0]);

let xhr = new XMLHttpRequest();
xhr.open('POST', 'upload_endpoint', true);
xhr.upload.onprogress = function(event) {
    if (event.lengthComputable) {
        let percentComplete = (event.loaded / event.total) * 100;
        console.log(`上傳進度: ${percentComplete.toFixed(2)}%`);
    }
};
xhr.onload = function() {
    console.log('文件已成功上傳');
};
xhr.send(formData);
```

## 解釋
### 常見問題
1. **無法計算進度**：當 `event.lengthComputable` 為 `false` 時，表示無法獲得總字節數，這通常發生在某些伺服器返回不正確的內容長度時。
   
2. **性能考量**：在大量數據傳輸時，頻繁的更新可能會導致性能問題，因此應該在進度更新中設置合理的頻率。

3. **跨域請求問題**：在進行跨域請求時，確保伺服器配置了正確的 CORS 標頭，以支持 `onprogress` 事件的正常運作。

## 總結
`onprogress` 事件是 JavaScript 中一個強大的工具，可以有效地監控和顯示數據加載進度，提升用戶體驗。