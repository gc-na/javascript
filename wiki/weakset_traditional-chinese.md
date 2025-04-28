<!--
Meta Description: # JavaScript WeakSet：深入了解其功能與應用 ## 摘要 WeakSet 是 JavaScript 中的一種集合類型，它允許您儲存弱引用的物件，這意味著當物件不再被引用時，垃圾回收器可以自動釋放這些物件的內存。 ## 文檔 ### 目的 WeakSet 主要用於存儲對物件的弱引用，...
Meta Keywords: weakset, has, let, value, console
-->

# JavaScript WeakSet：深入了解其功能與應用

## 摘要
WeakSet 是 JavaScript 中的一種集合類型，它允許您儲存弱引用的物件，這意味著當物件不再被引用時，垃圾回收器可以自動釋放這些物件的內存。

## 文檔
### 目的
WeakSet 主要用於存儲對物件的弱引用，這樣可以避免記憶體洩漏，因為 WeakSet 中的物件如果沒有其他引用，將自動被垃圾回收。這使得 WeakSet 特別適合用於存儲需要臨時存在的物件，如 DOM 元素或大量的資料結構。

### 使用方式
WeakSet 的基本語法如下：
```javascript
let weakset = new WeakSet([iterable]);
```
- `iterable`：可選的，表示可以用於初始化 WeakSet 的可迭代對象（如陣列）。

#### 主要方法
1. `add(value)`：將 `value` 加入到 WeakSet 中。
2. `delete(value)`：從 WeakSet 中刪除 `value`。
3. `has(value)`：檢查 WeakSet 是否包含 `value`。

### 詳細規範
- WeakSet 只能存儲物件，原始類型（如數字、字串）無法被添加。
- WeakSet 的大小無法計算，因為它不持有對物件的強引用。
- WeakSet 的迭代器（如 forEach）不可用，這是因為它的內容可能會隨著垃圾回收而變化。

## 範例
### 基本使用例子
```javascript
let obj1 = {};
let obj2 = {};
let weakset = new WeakSet([obj1]);

console.log(weakset.has(obj1)); // true
console.log(weakset.has(obj2)); // false

weakset.add(obj2);
console.log(weakset.has(obj2)); // true

weakset.delete(obj1);
console.log(weakset.has(obj1)); // false
```

### 物件的自動回收示例
```javascript
let weakset = new WeakSet();

{
    let obj = {};
    weakset.add(obj);
    console.log(weakset.has(obj)); // true
}
// obj 在此作用域外無其他引用，將被垃圾回收
console.log(weakset.has(obj)); // 可能是 false，因為 obj 可能已被回收
```

## 解釋
### 常見陷阱
1. **無法查詢大小**：WeakSet 不支援 `size` 屬性，因此無法直接獲得集合中物件的數量。
2. **無法迭代**：WeakSet 不能使用 forEach 或 for...of 進行迭代，這可能導致開發者誤解其用法。
3. **僅限於物件**：WeakSet 只能包含物件，這也意味著不能用來儲存原始類型的值。

### 附註
WeakSet 主要用於特定場景，如事件處理或臨時資料儲存。由於其弱引用的特性，使用時應謹慎考慮物件的生命週期。

## 一句話總結
WeakSet 是一種專為儲存弱引用物件而設計的集合類型，有助於自動管理記憶體。