<!--
Meta Description: # JavaScript Map 物件：用於儲存鍵值對的強大工具 ## 簡介 在 JavaScript 中，`Map` 是一種用於儲存鍵值對的集合，允許任何類型的鍵，包括物件。這使得 `Map` 成為一個靈活且高效的數據結構，特別是在需要在鍵與值之間快速查找時。 ## 文檔 ### 目的 `Map`...
Meta Keywords: map, mymap, key, javascript, set
-->

# JavaScript Map 物件：用於儲存鍵值對的強大工具

## 簡介
在 JavaScript 中，`Map` 是一種用於儲存鍵值對的集合，允許任何類型的鍵，包括物件。這使得 `Map` 成為一個靈活且高效的數據結構，特別是在需要在鍵與值之間快速查找時。

## 文檔
### 目的
`Map` 物件提供了有序的鍵值對集合，讓開發者能夠方便地進行數據操作和查詢。

### 使用方法
要使用 `Map`，可以透過 `new Map()` 來創建一個新的 Map 實例。以下是一些基本操作：
- **新增鍵值對**: 使用 `set(key, value)` 方法。
- **獲取值**: 使用 `get(key)` 方法。
- **檢查鍵是否存在**: 使用 `has(key)` 方法。
- **刪除鍵值對**: 使用 `delete(key)` 方法。
- **清空 Map**: 使用 `clear()` 方法。
- **獲取大小**: 使用 `size` 屬性來獲取 Map 中的元素數量。

### 詳細說明
`Map` 物件的主要特點包括：
- **鍵的類型**: 鍵可以是任何類型（包括對象、函數等）。
- **插入順序**: 鍵值對的插入順序會被保留，這意味著可以按插入的順序遍歷 `Map`。
- **可迭代性**: `Map` 物件是可迭代的，可以使用 `for...of` 循環或其他迭代工具進行遍歷。

## 範例
以下是一些 `Map` 的基本用法示例：

```javascript
// 創建一個新的 Map
const myMap = new Map();

// 新增鍵值對
myMap.set('name', 'Alice');
myMap.set('age', 30);
myMap.set('isStudent', false);

// 獲取值
console.log(myMap.get('name')); // 輸出: Alice

// 檢查鍵是否存在
console.log(myMap.has('age')); // 輸出: true

// 刪除鍵值對
myMap.delete('isStudent');

// 獲取大小
console.log(myMap.size); // 輸出: 2

// 遍歷 Map
myMap.forEach((value, key) => {
    console.log(`${key}: ${value}`);
});
```

## 解釋
使用 `Map` 時需要注意以下幾點：
- 鍵的重複性：如果使用相同的鍵來新增值，將會覆蓋舊的值。
- 性能：`Map` 在插入、刪除、查詢的性能上通常優於一般對象（Object），特別是在大量數據的情況下。
- 迭代順序：`Map` 會按照插入順序進行迭代，而對象的鍵值對並不保證順序。

## 總結
JavaScript 的 `Map` 物件是一個靈活且高效的資料結構，適合用於需要大量鍵值對操作的場景。