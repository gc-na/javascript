<!--
Meta Description: # JavaScript Promise：非同步操作的解決方案 ## 簡介 在JavaScript中，Promise是一種用來處理非同步操作的對象。它代表了一個可能在未來某個時間點完成或失敗的操作及其結果。 ## 文件說明 ### 目的 Promise旨在改善JavaScript的非同步行為，允許開...
Meta Keywords: resolve, promise, let, then, error
-->

# JavaScript Promise：非同步操作的解決方案

## 簡介
在JavaScript中，Promise是一種用來處理非同步操作的對象。它代表了一個可能在未來某個時間點完成或失敗的操作及其結果。

## 文件說明
### 目的
Promise旨在改善JavaScript的非同步行為，允許開發者以更可讀和可維護的方式處理非同步代碼。

### 使用方法
Promise有三種狀態：
1. **Pending（待定）**：初始狀態，既不是成功也不是失敗。
2. **Fulfilled（已成功）**：操作成功完成。
3. **Rejected（已失敗）**：操作失敗。

創建一個Promise對象的基本語法如下：
```javascript
let myPromise = new Promise((resolve, reject) => {
    // 非同步操作
    if (/* 操作成功 */) {
        resolve('成功的結果');
    } else {
        reject('失敗的原因');
    }
});
```

要使用Promise，可以調用`then()`和`catch()`方法：
```javascript
myPromise
    .then(result => {
        console.log(result); // 如果Promise成功
    })
    .catch(error => {
        console.error(error); // 如果Promise失敗
    });
```

## 示例
### 基本用法
```javascript
let fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        let success = true; // 模擬操作結果
        if (success) {
            resolve('數據獲取成功！');
        } else {
            reject('數據獲取失敗！');
        }
    }, 2000);
});

fetchData
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

### 使用Promise.all()
```javascript
let promise1 = Promise.resolve(3);
let promise2 = new Promise((resolve, reject) => {
    setTimeout(resolve, 100, 'foo');
});
let promise3 = 42;

Promise.all([promise1, promise2, promise3]).then(values => {
    console.log(values); // [3, "foo", 42]
});
```

## 解釋
### 常見陷阱
1. **未處理的拒絕**：如果不處理Promise的拒絕，會導致潛在的錯誤未被捕獲。務必使用`catch()`來捕獲錯誤。
2. **混合callback與Promise**：將Promise與傳統的回調函數混合使用可能會導致代碼難以閱讀，建議選擇一種風格進行操作。

### 額外提示
- 使用`async/await`可以使Promise的使用更加直觀，代碼更易於理解。
- Promise可以鏈接多個`then()`，每個`then()`都會返回一個新的Promise。

## 總結
Promise是JavaScript中處理非同步操作的一種強大工具，能夠使代碼更加清晰和可維護。