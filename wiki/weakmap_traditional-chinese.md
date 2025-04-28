<!--
Meta Description: # WeakMap：JavaScript 中的弱引用映射 ## 摘要 WeakMap 是 JavaScript 中一種特殊的集合，允許將物件作為鍵，並且不會阻止垃圾回收。這對於管理大數據結構和避免內存洩漏非常有用。 ## 文檔 ### 目的 WeakMap 提供了一種將物件作為鍵並存儲與之相關聯的值...
Meta Keywords: weakmap, obj, let, javascript, set
-->

# WeakMap：JavaScript 中的弱引用映射

## 摘要
WeakMap 是 JavaScript 中一種特殊的集合，允許將物件作為鍵，並且不會阻止垃圾回收。這對於管理大數據結構和避免內存洩漏非常有用。

## 文檔
### 目的
WeakMap 提供了一種將物件作為鍵並存儲與之相關聯的值的機制，這些鍵可以被垃圾回收，從而避免了內存洩漏的風險。

### 使用方法
WeakMap 的基本語法如下：
```javascript
let weakMap = new WeakMap();
```

#### 方法
- **set(key, value)**: 將指定的鍵和值添加到 WeakMap 中。
- **get(key)**: 根據鍵獲取對應的值，如果鍵不存在則返回 `undefined`。
- **has(key)**: 判斷 WeakMap 中是否存在指定的鍵。
- **delete(key)**: 刪除 WeakMap 中指定的鍵及其對應的值。

### 詳細說明
WeakMap 的鍵必須是物件類型，且當一個鍵沒有其他引用時，這個鍵及其對應的值會被垃圾回收。這使得 WeakMap 特別適合用於需要存儲私有數據的情況，例如在類或模組中。

```javascript
let obj = {};
let weakMap = new WeakMap();

weakMap.set(obj, "value");
console.log(weakMap.get(obj)); // "value"

obj = null; // obj 的引用被移除
// 此時 weakMap 中的鍵會自動被垃圾回收。
```

## 範例
### 基本用法
```javascript
let weakMap = new WeakMap();

let key1 = {};
let key2 = {};

weakMap.set(key1, "value1");
weakMap.set(key2, "value2");

console.log(weakMap.get(key1)); // 輸出: "value1"
console.log(weakMap.get(key2)); // 輸出: "value2"

weakMap.delete(key1);
console.log(weakMap.has(key1)); // 輸出: false
```

### 垃圾回收示例
```javascript
let weakMap = new WeakMap();

{
    let obj = {};
    weakMap.set(obj, "temporary value");
    console.log(weakMap.get(obj)); // 輸出: "temporary value"
}

// 這裡 obj 的引用已經被移除，WeakMap 中對應的鍵會被自動回收
```

## 解釋
- **常見陷阱**: 由於 WeakMap 的鍵必須是物件，不能使用原始類型（如字串、數字等）作為鍵。
- **無法遍歷**: WeakMap 不提供方法來遍歷其鍵或值，這意味著無法獲取所有鍵的列表。
- **不阻止垃圾回收**: 若 WeakMap 中的鍵沒有其他引用，這些鍵及其對應的值會自動被垃圾回收，這是它的一個主要特性。

## 一句話總結
WeakMap 是一種特殊的 JavaScript 集合，允許使用物件作為鍵並避免內存洩漏，適合存儲私有數據。