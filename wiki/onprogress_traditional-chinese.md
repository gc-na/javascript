<!--
Meta Description: # JavaScript 中的 onprogress 事件詳解 ## 簡介 `onprogress` 是一個重要的 JavaScript 事件，用於監控進度更新，尤其是在處理網絡請求和文件上傳下載時。這個事件可以幫助開發者提供即時的進度反饋，提升用戶體驗。 ## 文檔 ### 目的 `onprogr...
Meta Keywords: onprogress, xhr, lengthcomputable, event, javascript
-->

# JavaScript 中的 onprogress 事件詳解

## 簡介
`onprogress` 是一個重要的 JavaScript 事件，用於監控進度更新，尤其是在處理網絡請求和文件上傳下載時。這個事件可以幫助開發者提供即時的進度反饋，提升用戶體驗。

## 文檔
### 目的
`onprogress` 事件主要用於監控資源（如文件或數據）在下載或上傳過程中的進度。當資源的加載狀態發生變化時，會觸發這個事件，使開發者能夠實時更新用戶界面。

### 使用方法
`onprogress` 事件通常與 XMLHttpRequest 或 Fetch API 配合使用。開發者可以通過設定事件處理器來監聽進度事件，並根據進度更新 UI。

### 事件屬性
- **loaded**: 已加載的字節數。
- **total**: 預期的總字節數。
- **lengthComputable**: 布林值，指示是否可以計算總字節數。

### 例子
以下是使用 `XMLHttpRequest` 監控文件下載進度的基本範例：

```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://example.com/file.zip", true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`下載進度: ${percentComplete.toFixed(2)}%`);
    }
};

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log("文件下載完成!");
    }
};

xhr.send();
```

## 解釋
### 常見陷阱
1. **lengthComputable 為 false**: 在某些情況下，`lengthComputable` 可能返回 `false`，這意味著無法獲取總大小。開發者應考慮這種情況，並提供替代的用戶反饋。
   
2. **未正確設置事件處理器**: 確保在發送請求之前設置 `onprogress` 事件處理器，以避免錯過進度更新。

3. **過度依賴事件反饋**: 雖然 `onprogress` 事件提供了有用的進度信息，但在某些情況下，可能需要其他機制來確保用戶了解整體處理狀態。

## 一句總結
`onprogress` 事件讓開發者能夠有效地監控和反饋網絡請求的進度，從而改善用戶互動體驗。