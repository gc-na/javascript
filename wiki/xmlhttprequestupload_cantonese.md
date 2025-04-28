<!--
Meta Description: # XMLHttpRequestUpload：JavaScript 中的文件上傳管理器 ## 概要 `XMLHttpRequestUpload` 是一個 JavaScript 物件，專門用於管理通過 `XMLHttpRequest` 進行的文件上傳過程。它提供了有關上傳進度的事件，讓開發者能夠實時監...
Meta Keywords: xmlhttprequestupload, upload, event, xmlhttprequest, xhr
-->

# XMLHttpRequestUpload：JavaScript 中的文件上傳管理器

## 概要
`XMLHttpRequestUpload` 是一個 JavaScript 物件，專門用於管理通過 `XMLHttpRequest` 進行的文件上傳過程。它提供了有關上傳進度的事件，讓開發者能夠實時監控文件傳輸的狀態。

## 文檔
`XMLHttpRequestUpload` 物件主要用於處理上傳請求的進度和相關事件。當使用 `XMLHttpRequest` 進行文件上傳時，可以通過 `xhr.upload` 屬性獲取 `XMLHttpRequestUpload` 的實例。這個實例可以綁定多個事件處理器，以監控上傳過程的各個階段。

### 目的
`XMLHttpRequestUpload` 的主要目的是提供一個API，以便開發者可以輕鬆地跟踪文件上傳的進度，並在上傳過程中執行相應的操作。

### 使用方法
使用 `XMLHttpRequestUpload` 時，開發者需要執行以下步驟：

1. 創建一個 `XMLHttpRequest` 對象。
2. 獲取 `upload` 屬性，這是 `XMLHttpRequestUpload` 的實例。
3. 設置事件處理器，例如 `progress`、`load` 和 `error` 事件。
4. 使用 `send` 方法發送上傳請求。

## 示例
以下是 `XMLHttpRequestUpload` 的基本用法示例：

```javascript
// 創建 XMLHttpRequest 對象
var xhr = new XMLHttpRequest();

// 獲取 upload 屬性
var upload = xhr.upload;

// 設置進度事件的處理器
upload.addEventListener("progress", function(event) {
    if (event.lengthComputable) {
        var percentComplete = (event.loaded / event.total) * 100;
        console.log("上傳進度: " + percentComplete + "%");
    }
}, false);

// 設置完成事件的處理器
upload.addEventListener("load", function(event) {
    console.log("上傳完成！");
}, false);

// 設置錯誤事件的處理器
upload.addEventListener("error", function(event) {
    console.log("上傳失敗！");
}, false);

// 配置請求
xhr.open("POST", "/upload", true);
xhr.send(file); // file 是要上傳的檔案
```

## 解釋
在使用 `XMLHttpRequestUpload` 時，開發者需注意以下幾點：

- **事件處理器的順序**：確保在調用 `send` 方法之前已經設置好所有的事件處理器。
- **跨域請求**：在跨域上傳時，可能需要設置 CORS 標頭來允許上傳。
- **進度計算**：進度事件的 `loaded` 和 `total` 屬性用於計算上傳百分比，但在某些情況下（例如，伺服器未正確回應 Content-Length 標頭）可能會導致計算不準確。

## 一句總結
`XMLHttpRequestUpload` 是一個強大的工具，能夠監控和管理 JavaScript 中的文件上傳過程。