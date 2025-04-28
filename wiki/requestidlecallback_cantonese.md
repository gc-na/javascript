<!--
Meta Description: # requestIdleCallback：JavaScript 的空閒回調函數 ## 簡介 `requestIdleCallback` 是一個 JavaScript 的 API，用於在瀏覽器空閒時執行非緊急的任務。這個 API 讓開發者可以在不影響用戶體驗的情況下，利用瀏覽器的閒置時間來進行一些計...
Meta Keywords: requestidlecallback, javascript, api, myidlecallback, 是一個
-->

# requestIdleCallback：JavaScript 的空閒回調函數

## 簡介
`requestIdleCallback` 是一個 JavaScript 的 API，用於在瀏覽器空閒時執行非緊急的任務。這個 API 讓開發者可以在不影響用戶體驗的情況下，利用瀏覽器的閒置時間來進行一些計算或更新。

## 文檔
### 目的
`requestIdleCallback` 的主要目的是在瀏覽器的空閒時間執行回調函數，這樣可以避免阻塞主線程，從而提升應用程序的性能和響應速度。

### 用法
使用 `requestIdleCallback` 的基本語法如下：
```javascript
requestIdleCallback(callback, options);
```

- **callback**：一個函數，當瀏覽器處於空閒狀態時將被調用。
- **options**（可選）：一個包含 `timeout` 屬性的對象，用來設定回調函數的最長執行時間。

### 詳細信息
這個 API 會在瀏覽器的空閒時間內調用提供的回調函數，並且會傳遞一個 `IdleDeadline` 對象作為參數，該對象包含以下屬性：

- **timeRemaining()**：返回剩餘的空閒時間（以毫秒為單位）。
- **didTimeout**：一個布爾值，表示回調是否因超時而被調用。

## 範例
以下是使用 `requestIdleCallback` 的基本範例：

```javascript
function myIdleCallback(deadline) {
    while (deadline.timeRemaining() > 0) {
        // 執行非緊急的任務
        console.log('執行空閒任務');
    }
}

requestIdleCallback(myIdleCallback);
```

在這個例子中，當瀏覽器空閒時，`myIdleCallback` 會被調用，並執行一些非緊急的任務。

## 解釋
### 常見陷阱
1. **不保證執行**：如果瀏覽器在某個時刻沒有空閒時間，則回調函數可能不會被調用。
2. **超時設置**：如果設置了 `timeout`，且在指定時間內未執行，則回調會被強制執行，這可能會影響性能。

### 附加說明
- `requestIdleCallback` 主要用於改善用戶體驗，避免將重的計算放在主線程中，從而導致畫面卡頓。
- 這個 API 不支援某些舊版本的瀏覽器，因此在使用之前建議檢查兼容性。

## 一句話總結
`requestIdleCallback` 是一個 JavaScript API，用於在瀏覽器空閒時執行非緊急任務，有助於提升網頁性能及用戶體驗。