<!--
Meta Description: # JavaScript 中的 Set：集合資料結構的完整指南 ## 簡介 Set 是 JavaScript 提供的一種內建資料結構，用於儲存不重複的值。這使得 Set 成為處理唯一性資料的理想選擇。無論是在處理數字、字串還是物件，Set 都能有效地管理和操作這些資料。 ## 文件說明 Set 的目...
Meta Keywords: set, fruits, size, console, log
-->

# JavaScript 中的 Set：集合資料結構的完整指南

## 簡介
Set 是 JavaScript 提供的一種內建資料結構，用於儲存不重複的值。這使得 Set 成為處理唯一性資料的理想選擇。無論是在處理數字、字串還是物件，Set 都能有效地管理和操作這些資料。

## 文件說明
Set 的目的是提供一個可以儲存任何類型的唯一值的集合。與陣列不同，Set 會自動排除重複的元素，這使得對於需要確保資料唯一性的場景來說，Set 是非常有用的。

### 使用方式
要創建一個 Set，你可以使用以下語法：

```javascript
const mySet = new Set([iterable]);
```

這裡的 `iterable` 可以是任何可迭代的物件，如陣列或字串。若未提供 `iterable`，則創建一個空的 Set。

### 主要方法
- **add(value)**: 向 Set 中添加一個新元素。
- **delete(value)**: 從 Set 中刪除一個元素。
- **has(value)**: 判斷 Set 中是否包含某個元素，返回布林值。
- **clear()**: 清空 Set 中的所有元素。
- **size**: 返回 Set 中的元素數量。

## 範例
以下是一些使用 Set 的基本範例：

```javascript
// 創建一個 Set
const fruits = new Set(['apple', 'banana', 'orange']);
console.log(fruits.size); // 輸出: 3

// 增加元素
fruits.add('mango');
console.log(fruits.size); // 輸出: 4

// 嘗試添加重複的元素
fruits.add('apple'); 
console.log(fruits.size); // 輸出: 4 (不重複)

// 檢查元素存在性
console.log(fruits.has('banana')); // 輸出: true

// 刪除元素
fruits.delete('orange');
console.log(fruits.size); // 輸出: 3

// 清空 Set
fruits.clear();
console.log(fruits.size); // 輸出: 0
```

## 解釋
在使用 Set 時，有幾個常見的注意事項：
- Set 中的元素是唯一的，因此試圖添加重複元素將不會改變 Set 的內容。
- Set 會根據引用比較物件，這意味著兩個具有相同內容的物件仍然被視為不同的元素。
- 當使用 Set 進行迭代時，元素的順序是根據它們被添加的順序。

## 單行摘要
Set 是 JavaScript 中一種用於儲存唯一值的資料結構，適合管理不重複的資料。