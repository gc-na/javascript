<!--
Meta Description: # JavaScript 中的 Fence：概述與應用 ## 簡介 Fence（圍欄）是一種在 JavaScript 中的設計模式，主要用於控制和管理異步操作的執行。透過 Fence，我們可以有效地限制同時執行的任務數量，從而避免資源過度消耗和潛在的性能問題。 ## 文檔 ### 目的 Fence ...
Meta Keywords: fence, javascript, promise, maxconcurrent, currentlyrunning
-->

# JavaScript 中的 Fence：概述與應用

## 簡介
Fence（圍欄）是一種在 JavaScript 中的設計模式，主要用於控制和管理異步操作的執行。透過 Fence，我們可以有效地限制同時執行的任務數量，從而避免資源過度消耗和潛在的性能問題。

## 文檔
### 目的
Fence 模式旨在提供一個簡單的方式來管理併發操作，特別是在處理大量的異步請求時，能夠有效控制同時執行的請求數。

### 使用方式
在 JavaScript 中，Fence 通常與 Promise 結合使用，以確保在特定時間內不會啟動超過預設數量的併發請求。實現時，可以創建一個函數來追蹤當前正在執行的任務數量，並在任務完成時釋放一個空位。

### 詳細信息
1. **初始化**: 定義最大併發數量。
2. **添加任務**: 每當添加一個任務時，檢查當前執行的任務數量。
3. **執行任務**: 當有空閒位時，開始執行新的任務。
4. **完成任務**: 一旦任務完成，更新當前執行的任務數，並檢查是否有等待中的任務可以啟動。

## 範例
以下是一個簡單的 Fence 實現範例：

```javascript
class Fence {
    constructor(maxConcurrent) {
        this.maxConcurrent = maxConcurrent;
        this.currentlyRunning = 0;
        this.queue = [];
    }

    run(task) {
        return new Promise((resolve, reject) => {
            this.queue.push(() => task().then(resolve).catch(reject));
            this.execute();
        });
    }

    execute() {
        while (this.currentlyRunning < this.maxConcurrent && this.queue.length > 0) {
            const nextTask = this.queue.shift();
            this.currentlyRunning++;
            nextTask().finally(() => {
                this.currentlyRunning--;
                this.execute();
            });
        }
    }
}

// 使用範例
const fence = new Fence(2); // 設定最大併發數為 2
const task = () => new Promise(res => setTimeout(res, 1000));

for (let i = 0; i < 5; i++) {
    fence.run(task).then(() => console.log(`任務 ${i} 完成`));
}
```

## 解釋
在使用 Fence 模式時，開發者應注意以下幾點：
- **任務排隊**: 當任務數量超過併發限制時，新的任務會被排隊，這可能導致延遲。
- **錯誤處理**: 確保在任務執行過程中正確處理異常，避免未處理的 Promise 拋出錯誤。
- **性能調試**: 在高併發情況下，需定期檢查性能，確保不會因為過度排隊而導致性能下降。

## 總結
Fence 模式是一種有效的異步操作管理工具，能夠幫助開發者控制同時執行的任務數量，從而提升應用的性能和穩定性。