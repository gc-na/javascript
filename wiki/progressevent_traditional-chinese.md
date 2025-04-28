<!--
Meta Description: # ProgressEvent 在 JavaScript 中的應用與使用 ## 概述 ProgressEvent 是 JavaScript 中一個重要的事件類型，主要用於反映某些操作（如下載或上傳過程）的進度。它與 XMLHttpRequest、Fetch API 和其他可進行進度跟蹤的 API 紧...
Meta Keywords: progressevent, xhr, event, const, javascript
-->

# ProgressEvent 在 JavaScript 中的應用與使用

## 概述
ProgressEvent 是 JavaScript 中一個重要的事件類型，主要用於反映某些操作（如下載或上傳過程）的進度。它與 XMLHttpRequest、Fetch API 和其他可進行進度跟蹤的 API 紧密相關。

## 文件說明

### 目的
ProgressEvent 允許開發者監控進度事件，這些事件在處理大型數據傳輸時非常有用。它提供了有關進度的詳細信息，例如已加載的字節數和總字節數。

### 使用方法
ProgressEvent 事件通常與以下對象一起使用：

- `XMLHttpRequest`
- `Fetch API`
- `FileReader`

這些對象在執行文件上傳或數據下載時，會觸發 ProgressEvent。

### 事件屬性
ProgressEvent 提供了幾個重要屬性：
- `loaded`：已加載的字節數。
- `total`：總字節數（如果已知）。
- `lengthComputable`：一個布林值，指示是否可以計算傳輸的總長度。

### 註冊事件
使用 `addEventListener` 方法可以註冊 ProgressEvent 的監聽器。例如：

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'path/to/resource');

xhr.addEventListener('progress', (event) => {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`載入進度: ${percentComplete}%`);
    }
});

xhr.send();
```

## 範例

### 基本範例：使用 XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/largefile');

xhr.addEventListener('progress', (event) => {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`載入進度: ${percentComplete}%`);
    }
});

xhr.onload = () => {
    console.log('載入完成');
};

xhr.send();
```

### 使用 Fetch API
```javascript
async function fetchData() {
    const response = await fetch('https://example.com/largefile');
    const reader = response.body.getReader();
    let totalBytes = 0;
    
    while (true) {
        const { done, value } = await reader.read();
        if (done) break;
        totalBytes += value.length;
        console.log(`已接收字節: ${totalBytes}`);
    }
    console.log('數據接收完成');
}

fetchData();
```

## 解釋
在使用 ProgressEvent 時，開發者常常會遇到一些常見的陷阱：

1. **lengthComputable 屬性**：並非所有的請求都會提供這個屬性，對於某些請求，`total` 可能是 `undefined`。這意味著無法計算進度百分比。

2. **事件觸發頻率**：ProgressEvent 會頻繁觸發，因此在事件處理函數中進行性能優化是必要的，以避免過多的 DOM 更新或計算。

3. **跨域請求**：在跨域請求的情況下，可能會受到 CORS 的限制，這可能會影響進度事件的觸發。

## 一句話總結
ProgressEvent 允許 JavaScript 開發者監控和管理文件上傳和下載的進度，提供有用的進度信息。