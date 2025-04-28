<!--
Meta Description: # JavaScript Worker（工作者）: 提升網頁效能的多執行緒技術 ## 概述 JavaScript Worker 是一種允許在背景執行多執行緒任務的技術。它使得開發者可以在不阻塞主執行緒的情況下，執行長時間運行的任務，從而提升網頁的響應性和效能。 ## 文件說明 JavaScript ...
Meta Keywords: worker, javascript, postmessage, onmessage, myworker
-->

# JavaScript Worker（工作者）: 提升網頁效能的多執行緒技術

## 概述
JavaScript Worker 是一種允許在背景執行多執行緒任務的技術。它使得開發者可以在不阻塞主執行緒的情況下，執行長時間運行的任務，從而提升網頁的響應性和效能。

## 文件說明
JavaScript Worker 的主要目的是提供一個獨立的執行環境，讓開發者可以在該環境中執行計算密集型或時間較長的操作，而不會影響到使用者界面的流暢度。這是透過以下幾個步驟來實現的：

1. **創建 Worker**：使用 `Worker` 構造函數來創建一個新的 Worker 實例，並指定要執行的 JavaScript 檔案。
2. **通訊**：主執行緒和 Worker 之間可以透過 `postMessage()` 方法發送消息，並使用 `onmessage` 事件接收回應。
3. **終止 Worker**：當任務完成後，可以使用 `terminate()` 方法來停止 Worker 的執行。

### 使用範例
```javascript
// main.js
const myWorker = new Worker('worker.js');

myWorker.postMessage('開始計算');

myWorker.onmessage = function(event) {
    console.log('接收到結果: ', event.data);
};

// worker.js
onmessage = function(event) {
    // 模擬計算
    let result = 0;
    for (let i = 0; i < 1000000000; i++) {
        result += i;
    }
    postMessage(result);
};
```

## 解釋
使用 JavaScript Worker 時，有幾個常見的陷阱和注意事項：

1. **資料傳遞限制**：Worker 只能接收可序列化的資料，若傳遞不支持的資料類型（如 DOM 元素），將會導致錯誤。
2. **同源政策**：Worker 載入的腳本必須遵從同源政策，否則將無法正常運行。
3. **錯誤處理**：Worker 內的錯誤需要透過 `onerror` 事件來捕捉，否則將無法顯示錯誤信息。

## 總結
JavaScript Worker 是一種強大的工具，可以有效地利用多執行緒來提升網頁性能，特別是在執行計算密集型任務時。透過適當的使用方式，可以避免主執行緒的阻塞，從而提供更好的使用者體驗。