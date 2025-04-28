<!--
Meta Description: # 清除計時器：JavaScript 中的 clearInterval 函數 ## 簡介 `clearInterval` 是 JavaScript 中用於停止由 `setInterval` 設置的計時器的函數。這個函數在處理重複性任務時非常有用，特別是在需要控制事件發生頻率的情況下。 ## 文檔 #...
Meta Keywords: clearinterval, setinterval, intervalid, javascript, count
-->

# 清除計時器：JavaScript 中的 clearInterval 函數

## 簡介
`clearInterval` 是 JavaScript 中用於停止由 `setInterval` 設置的計時器的函數。這個函數在處理重複性任務時非常有用，特別是在需要控制事件發生頻率的情況下。

## 文檔
### 目的
`clearInterval` 的主要目的是停止一個先前通過 `setInterval` 創建的計時器，從而避免不再需要的重複執行。

### 使用方法
```javascript
clearInterval(intervalID);
```
- **intervalID**：這是一個整數，表示之前由 `setInterval` 返回的計時器 ID。這個 ID 用於識別要清除的計時器。

### 詳細說明
1. **設置計時器**：使用 `setInterval` 創建一個計時器，它會在指定的時間間隔內重複執行一個函數或代碼片段。
2. **清除計時器**：當不再需要這個計時器時，使用 `clearInterval` 並傳入相應的計時器 ID，以停止該計時器。

## 範例
### 基本用法
以下是如何使用 `setInterval` 和 `clearInterval` 的簡單範例：

```javascript
let count = 0;
const intervalID = setInterval(() => {
    count++;
    console.log(`計數：${count}`);
    
    if (count === 5) {
        clearInterval(intervalID); // 停止計時器
        console.log("計時器已停止");
    }
}, 1000);
```

在這個例子中，每秒計數一次，當計數達到 5 時，計時器停止。

## 解釋
- **常見陷阱**：如果傳入的 `intervalID` 無效或不存在，`clearInterval` 不會報錯，但計時器也不會被清除。
- **多次清除**：多次調用 `clearInterval` 不會導致錯誤，若計時器已經停止，後續調用不會有任何影響。
- **作用範圍**：請確保 `intervalID` 在當前作用域中可用，否則將無法正確清除計時器。

## 一句總結
`clearInterval` 是用於停止由 `setInterval` 創建的計時器的函數，確保不再需要的重複操作不會繼續執行。