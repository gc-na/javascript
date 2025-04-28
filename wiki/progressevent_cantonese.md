<!--
Meta Description: # ProgressEvent: JavaScript中的進度事件 ## 概要 ProgressEvent 是一個用於監控異步操作進度的事件，特別是在處理網絡請求或文件上傳時非常有用。 ## 文檔 ### 目的 ProgressEvent 提供了一種方法來跟踪某個操作的進度，比如 XMLHttpRe...
Meta Keywords: const, progressevent, fetch, api, lengthcomputable
-->

# ProgressEvent: JavaScript中的進度事件

## 概要
ProgressEvent 是一個用於監控異步操作進度的事件，特別是在處理網絡請求或文件上傳時非常有用。

## 文檔
### 目的
ProgressEvent 提供了一種方法來跟踪某個操作的進度，比如 XMLHttpRequest 或 Fetch API 的請求，或是 File API 中的文件上傳。這使得開發者可以在操作進行時給用戶提供反饋。

### 用法
ProgressEvent 可以在各種情況下被觸發，主要用於以下情境：
- 當 XMLHttpRequest 對象進行請求時。
- 當使用 Fetch API 時，結合 ReadableStream 可以獲得進度。
- 當文件上傳或下載時。

### 事件屬性
- **lengthComputable**: 一個布爾值，指示當前操作的總長度是否可以計算。
- **loaded**: 已加載的字節數。
- **total**: 總的字節數，僅在 `lengthComputable` 為 `true` 時有效。

## 例子
### 基本用法
這裡是一個使用 XMLHttpRequest 的示例，來展示如何使用 ProgressEvent 來顯示上傳進度：

```javascript
const xhr = new XMLHttpRequest();
xhr.open("POST", "upload.php", true);

// 監聽進度事件
xhr.upload.addEventListener("progress", function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`上傳進度: ${percentComplete.toFixed(2)}%`);
    }
});

// 發送請求
xhr.send(formData);
```

### 使用 Fetch API
利用 Fetch API 並結合流來獲取進度：

```javascript
async function uploadFile(file) {
    const response = await fetch('upload.php', {
        method: 'POST',
        body: file
    });

    const reader = response.body.getReader();
    const contentLength = +response.headers.get('Content-Length');

    let receivedLength = 0; // 目前接收的字節數
    while (true) {
        const { done, value } = await reader.read();
        if (done) {
            break;
        }
        receivedLength += value.length;
        const percentComplete = (receivedLength / contentLength) * 100;
        console.log(`下載進度: ${percentComplete.toFixed(2)}%`);
    }
}
```

## 解釋
### 常見陷阱
- **lengthComputable**: 並非所有的操作都能計算總長度，因此在使用 `loaded` 和 `total` 時，必須先檢查 `lengthComputable` 是否為 `true`。
- **跨域請求**: 如果進行跨域請求，必須確保服務器端設置了正確的 CORS 標頭，否則將無法接收到進度事件。

### 附加說明
進度事件主要用於提升用戶體驗，特別是在處理大型文件或網絡請求時。適當地使用進度事件可以提供即時反饋，增加應用的交互性。

## 一行總結
ProgressEvent 是一個用於監控異步操作進度的事件，特別適合用於網絡請求和文件上傳。