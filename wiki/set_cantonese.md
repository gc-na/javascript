<!--
Meta Description: # JavaScript 的 Set：用於唯一值的集合 ## 概述 JavaScript 的 Set 是一種用於存儲唯一值的集合資料結構，無論是原始值還是對象引用。Set 提供了高效的操作來添加、刪除和檢查元素，並且可以用於實現不重複的數據項目。 ## 文檔 ### 目的 Set 旨在提供一個簡單的...
Meta Keywords: set, javascript, numbers, console, log
-->

# JavaScript 的 Set：用於唯一值的集合

## 概述
JavaScript 的 Set 是一種用於存儲唯一值的集合資料結構，無論是原始值還是對象引用。Set 提供了高效的操作來添加、刪除和檢查元素，並且可以用於實現不重複的數據項目。

## 文檔
### 目的
Set 旨在提供一個簡單的方法來管理和操作唯一的數據集合，避免數據重複。這使得在處理大量數據時更為高效，特別是在需要進行查找和去重操作時。

### 使用方法
在 JavaScript 中，Set 是一個內建的對象，可以通過 `new Set()` 來創建一個新的 Set 實例。

#### 基本語法
```javascript
const mySet = new Set([iterable]);
```
- `iterable` 可選，是一個可迭代對象（如陣列），用於初始化 Set。

### 方法
- `add(value)`: 向 Set 添加一個新的元素。
- `delete(value)`: 刪除 Set 中特定的元素。
- `has(value)`: 判斷 Set 中是否存在特定的元素，返回布林值。
- `clear()`: 清空 Set 中的所有元素。
- `size`: 返回 Set 中的元素數量。

## 範例
### 創建一個 Set
```javascript
const numbers = new Set([1, 2, 3, 4, 5]);
console.log(numbers); // Set { 1, 2, 3, 4, 5 }
```

### 添加元素
```javascript
numbers.add(6);
console.log(numbers); // Set { 1, 2, 3, 4, 5, 6 }
```

### 刪除元素
```javascript
numbers.delete(3);
console.log(numbers); // Set { 1, 2, 4, 5, 6 }
```

### 檢查是否存在元素
```javascript
console.log(numbers.has(2)); // true
console.log(numbers.has(3)); // false
```

### 清空 Set
```javascript
numbers.clear();
console.log(numbers); // Set {}
```

## 解釋
在使用 Set 的過程中，有幾個常見的陷阱需要注意：
- Set 只會儲存唯一值，因此添加重複的值不會導致錯誤，但也不會改變 Set 的內容。
- 對於對象和陣列，Set 會根據引用來判斷唯一性，而不是根據內容。例如，即使兩個對象的內容相同，它們仍然被視為不同的元素。
- Set 的迭代順序是根據元素的插入順序，因此可以使用 `for...of` 迴圈來遍歷。

## 總結
JavaScript 的 Set 提供了一種高效的方式來儲存和管理唯一值，適合用於需要去重和快速查找的場景。