<!--
Meta Description: # XMLHttpRequestUpload：在 JavaScript 中的上傳功能 ## 概述 `XMLHttpRequestUpload` 是一個在 JavaScript 中用於處理檔案上傳的物件，通常與 `XMLHttpRequest` 一起使用。它提供了一系列事件來監控上傳進度，為用戶提供即...
Meta Keywords: event, upload, xhr, const, addeventlistener
-->

# XMLHttpRequestUpload：在 JavaScript 中的上傳功能

## 概述
`XMLHttpRequestUpload` 是一個在 JavaScript 中用於處理檔案上傳的物件，通常與 `XMLHttpRequest` 一起使用。它提供了一系列事件來監控上傳進度，為用戶提供即時的上傳狀態反饋。

## 文檔
`XMLHttpRequestUpload` 的主要目的是允許開發者監控和管理檔案上傳過程。這個物件的實例可以通過 `XMLHttpRequest.upload` 獲得。開發者可以使用此物件來註冊事件監聽器，以獲取上傳的進度、完成狀態以及錯誤信息。

### 用法
```javascript
const xhr = new XMLHttpRequest();
const upload = xhr.upload;

upload.addEventListener("progress", function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`上傳進度: ${percentComplete}%`);
    }
}, false);

upload.addEventListener("load", function() {
    console.log("檔案上傳完成！");
}, false);

upload.addEventListener("error", function() {
    console.log("檔案上傳失敗！");
}, false);

upload.addEventListener("abort", function() {
    console.log("檔案上傳已中止！");
}, false);

// 開始上傳檔案
xhr.open("POST", "上傳端點");
xhr.send(formData);
```

## 示例
### 基本使用範例
```javascript
const form = document.getElementById("uploadForm");
const xhr = new XMLHttpRequest();

form.addEventListener("submit", function(event) {
    event.preventDefault();
    const formData = new FormData(form);
    
    xhr.open("POST", "你的上傳端點");
    
    xhr.upload.addEventListener("progress", function(event) {
        if (event.lengthComputable) {
            const percentComplete = (event.loaded / event.total) * 100;
            console.log(`上傳進度: ${percentComplete}%`);
        }
    });

    xhr.send(formData);
});
```

## 解釋
在使用 `XMLHttpRequestUpload` 時，開發者應注意以下幾點：
- **事件處理**：確保所有需要的事件（如 `progress`、`load`、`error` 和 `abort`）都已正確註冊，這樣才能獲得上傳的完整狀態。
- **跨域請求**：如果上傳的網址與當前網站不同，可能需要處理 CORS（跨源資源共享）問題。
- **檔案大小限制**：某些伺服器可能對上傳檔案的大小有限制，開發者需提前確認。

## 一句總結
`XMLHttpRequestUpload` 是一個強大的 JavaScript 物件，用於監控和管理檔案上傳過程，提供即時的進度反饋和錯誤處理。