<!--
Meta Description: # JavaScript Promise：非同步處理的最佳解決方案 ## 簡介 JavaScript 的 Promise 是一種用於處理非同步操作的對象，提供了一種更清晰和可讀的方式來處理回調函數，以避免回調地獄（callback hell）的問題。 ## 文件說明 ### 目的 Promise 旨...
Meta Keywords: promise, javascript, then, error, data
-->

# JavaScript Promise：非同步處理的最佳解決方案

## 簡介
JavaScript 的 Promise 是一種用於處理非同步操作的對象，提供了一種更清晰和可讀的方式來處理回調函數，以避免回調地獄（callback hell）的問題。

## 文件說明
### 目的
Promise 旨在簡化非同步編程，允許開發者在操作執行完成後進行鏈式調用，從而提高代碼的可讀性和可維護性。

### 使用方式
Promise 的基本用法如下：
```javascript
let promise = new Promise((resolve, reject) => {
    // 執行非同步操作
    if (/* 操作成功 */) {
        resolve("成功的結果");
    } else {
        reject("失敗的原因");
    }
});

// 使用 then() 和 catch() 處理結果
promise.then((result) => {
    console.log(result); // 處理成功結果
}).catch((error) => {
    console.error(error); // 處理錯誤
});
```

### 詳細說明
1. **狀態**：Promise 對象有三種狀態：
   - **Pending**（待定）：初始狀態，既不是成功也不是失敗。
   - **Fulfilled**（已實現）：操作成功完成。
   - **Rejected**（已拒絕）：操作失敗。

2. **方法**：
   - **then(onFulfilled, onRejected)**：添加成功和失敗的處理函數，返回一個新的 Promise。
   - **catch(onRejected)**：添加失敗的處理函數，返回一個新的 Promise。
   - **finally(onFinally)**：添加不論成功或失敗都會執行的函數，返回一個新的 Promise。

## 範例
### 範例 1：基本用法
```javascript
let fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        const data = "這是從伺服器獲取的數據";
        resolve(data);
    }, 2000);
});

fetchData.then((data) => {
    console.log(data); // 輸出：這是從伺服器獲取的數據
});
```

### 範例 2：錯誤處理
```javascript
let fetchDataWithError = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("伺服器錯誤");
    }, 2000);
});

fetchDataWithError
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.error(error); // 輸出：伺服器錯誤
    });
```

## 解釋
### 常見陷阱
- **未處理的拒絕**：如果 Promise 被拒絕而沒有捕獲錯誤，則會導致未處理的拒絕警告。應該始終使用 `.catch()` 方法來處理可能的錯誤。
- **鏈式調用**：當使用鏈式調用時，每個 `then()` 方法都會返回一個新的 Promise，這意味著你可以在每個步驟中處理不同的結果或錯誤，這同時也可能導致錯誤的管理變得複雜。

## 單行總結
JavaScript 的 Promise 提供了一種優雅的方式來處理非同步操作，使代碼更加清晰和可維護。