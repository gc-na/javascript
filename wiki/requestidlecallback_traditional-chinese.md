<!--
Meta Description: # requestIdleCallback：JavaScript 的非同步任務處理 ## 簡介 `requestIdleCallback` 是一個 JavaScript API，允許開發者在瀏覽器空閒時執行任務，這樣能夠有效地利用空閒時間來提升應用程式的效能和使用者體驗。 ## 文檔 ### 目的 ...
Meta Keywords: requestidlecallback, javascript, callback, myidlecallback, deadline
-->

# requestIdleCallback：JavaScript 的非同步任務處理

## 簡介
`requestIdleCallback` 是一個 JavaScript API，允許開發者在瀏覽器空閒時執行任務，這樣能夠有效地利用空閒時間來提升應用程式的效能和使用者體驗。

## 文檔
### 目的
`requestIdleCallback` 主要用於在瀏覽器沒有忙碌處理任務時執行非緊急的工作，例如更新畫面、執行後台計算或載入資料等，進而減少對主執行緒的阻塞。

### 使用方式
`requestIdleCallback` 的基本語法如下：

```javascript
requestIdleCallback(callback, options);
```

- **callback**: 一個函數，當瀏覽器進入空閒狀態時會被執行。
- **options**: 一個可選的物件，可以包含以下屬性：
  - **timeout**: 指定 callback 最長可以等待的時間（以毫秒為單位），超過這個時間後，callback 還是會被執行。

### 返回值
`requestIdleCallback` 返回一個唯一的識別碼，可以用來取消該回調。

## 範例
### 基本使用範例
以下是一個使用 `requestIdleCallback` 的簡單範例：

```javascript
function myIdleCallback(deadline) {
    while (deadline.timeRemaining() > 0) {
        // 進行一些非緊急的任務
        console.log('執行非緊急任務');
    }
}

// 註冊空閒回調
requestIdleCallback(myIdleCallback);
```

### 加入超時選項
以下範例展示如何使用超時參數：

```javascript
function myIdleCallback(deadline) {
    while (deadline.timeRemaining() > 0) {
        console.log('執行非緊急任務');
    }
}

// 註冊空閒回調，並設置超時為 100 毫秒
requestIdleCallback(myIdleCallback, { timeout: 100 });
```

## 解釋
### 常見陷阱
1. **主執行緒的阻塞**: `requestIdleCallback` 只在主執行緒空閒時執行。如果主執行緒被阻塞，callback 將不會被調用。
2. **不保證立即執行**: `requestIdleCallback` 可能不會立即執行，這取決於瀏覽器的執行環境和其他任務的優先級。
3. **不支持的瀏覽器**: 某些舊版本的瀏覽器可能不支持 `requestIdleCallback`，需要檢查兼容性。

## 總結
`requestIdleCallback` 是一個強大的工具，可以幫助開發者在瀏覽器空閒時執行非緊急任務，從而改善應用程式的效能和用戶體驗。