<!--
Meta Description: # Atomics：JavaScript 中的原子操作 ## 簡介 Atomics 是一組 JavaScript API，允許在 Web Workers 和 SharedArrayBuffer 之間進行安全的原子操作。這些原子操作能夠避免多執行緒環境下的數據競爭，確保數據一致性。 ## 文檔 ###...
Meta Keywords: atomics, int32view, sharedarraybuffer, typedarray, index
-->

# Atomics：JavaScript 中的原子操作

## 簡介
Atomics 是一組 JavaScript API，允許在 Web Workers 和 SharedArrayBuffer 之間進行安全的原子操作。這些原子操作能夠避免多執行緒環境下的數據競爭，確保數據一致性。

## 文檔
### 目的
Atomics 提供了一種安全的方式來在共享緩衝區中進行操作，這對於需要在多個執行緒之間進行協作的應用程式非常重要。透過使用 Atomics，開發者可以避免傳統的鎖機制，從而提高性能。

### 用法
Atomics 涉及以下幾個主要方法：
- `Atomics.add()`
- `Atomics.sub()`
- `Atomics.and()`
- `Atomics.or()`
- `Atomics.xor()`
- `Atomics.exchange()`
- `Atomics.compareExchange()`
- `Atomics.load()`
- `Atomics.store()`
- `Atomics.wait()`
- `Atomics.notify()`

這些方法通常用於操作 `SharedArrayBuffer` 中的整數值，確保這些操作是原子的，即不會被其他執行緒中斷。

### 詳細說明
每個 Atomics 方法都有其特定的功能。以下是幾個常見方法的簡要介紹：

- **Atomics.add(typedArray, index, value)**：將指定位置的值增加給定的數值，並返回原始值。
- **Atomics.load(typedArray, index)**：讀取指定位置的值。
- **Atomics.store(typedArray, index, value)**：將指定值寫入到指定位置。
- **Atomics.wait(typedArray, index, value, timeout)**：使當前執行緒等待，直到指定位置的值變為期望的值。
- **Atomics.notify(typedArray, index, count)**：喚醒在指定位置等待的執行緒。

## 範例
以下是使用 Atomics 的基本範例：

```javascript
// 創建一個 SharedArrayBuffer 和一個視圖
const sharedBuffer = new SharedArrayBuffer(4);
const int32View = new Int32Array(sharedBuffer);

// 使用 Atomics 方法
Atomics.store(int32View, 0, 10);
console.log(Atomics.load(int32View, 0)); // 輸出：10

Atomics.add(int32View, 0, 5);
console.log(Atomics.load(int32View, 0)); // 輸出：15

// 等待和通知範例
Atomics.wait(int32View, 0, 15);
console.log('Thread notified!');
```

## 解釋
在使用 Atomics 時，開發者需要注意以下幾點：
- Atomics 僅能在 Web Workers 和 SharedArrayBuffer 中使用，不能在主執行緒中直接操作。
- 確保操作的整數值是 32 位的，因為 Atomics 僅支持此類型的操作。
- 在多執行緒環境中，使用 Atomics 時，需要小心避免死鎖和競爭條件。

## 總結
Atomics 為 JavaScript 提供了高效且安全的原子操作，特別適用於多執行緒環境中的數據共享和協作。