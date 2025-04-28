<!--
Meta Description: # JavaScript WeakMap：深入淺出及其應用指南 ## 概述 WeakMap 是 JavaScript 的一種內建資料結構，允許以物件作為鍵，並且其鍵的引用是弱引用，這意味著當沒有其他引用時，WeakMap 可以自動釋放鍵所佔用的記憶體空間。 ## 文件說明 WeakMap 的主要目的...
Meta Keywords: weakmap, obj1, key, console, log
-->

# JavaScript WeakMap：深入淺出及其應用指南

## 概述
WeakMap 是 JavaScript 的一種內建資料結構，允許以物件作為鍵，並且其鍵的引用是弱引用，這意味著當沒有其他引用時，WeakMap 可以自動釋放鍵所佔用的記憶體空間。

## 文件說明
WeakMap 的主要目的是提供一個可以存儲物件鍵-值對的集合，而不會阻止垃圾回收器回收不再使用的物件。這使得 WeakMap 特別適合用於需要臨時存儲資料的場景，例如在物件上掛載私有數據。

### 用法
WeakMap 的基本用法如下：
- **創建 WeakMap**: 使用 `new WeakMap()` 來創建一個新的 WeakMap 實例。
- **添加鍵-值對**: 使用 `set(key, value)` 方法來添加鍵-值對，其中 `key` 必須是一個物件。
- **獲取值**: 使用 `get(key)` 方法來獲取對應於鍵的值。
- **檢查鍵是否存在**: 使用 `has(key)` 方法來檢查 WeakMap 中是否存在指定的鍵。
- **刪除鍵-值對**: 使用 `delete(key)` 方法來刪除指定的鍵-值對。

### 詳細說明
WeakMap 主要有以下特性：
- **鍵必須是物件**: WeakMap 的鍵僅限於物件類型，不能是基本數據類型（如字符串或數字）。
- **弱引用**: WeakMap 中的物件鍵是弱引用，當沒有其他引用指向該物件時，該物件會被垃圾收集。
- **不可遍歷**: WeakMap 不支持任何遍歷方法，如 `forEach`，因此無法列出所有的鍵或值。
  
## 例子
### 基本用法示例
```javascript
// 創建一個 WeakMap
const weakMap = new WeakMap();

// 創建一個物件作為鍵
const obj1 = {};
const obj2 = {};

// 設置鍵-值對
weakMap.set(obj1, 'Hello');
weakMap.set(obj2, 'World');

// 獲取值
console.log(weakMap.get(obj1)); // 輸出: Hello
console.log(weakMap.get(obj2)); // 輸出: World

// 檢查鍵是否存在
console.log(weakMap.has(obj1)); // 輸出: true
console.log(weakMap.has({}));    // 輸出: false

// 刪除鍵-值對
weakMap.delete(obj1);
console.log(weakMap.has(obj1)); // 輸出: false
```

## 解釋
在使用 WeakMap 時，開發者可能會遇到以下問題：
- **物件引用問題**: 如果一個物件沒有其他引用，則 WeakMap 中的鍵會自動被垃圾收集。這意味著在某些情況下，你可能會發現你已經無法從 WeakMap 中獲取這些鍵的值。
- **無法遍歷**: 因為 WeakMap 不能被遍歷，所以無法直接列出所有的鍵或值。如果需要遍歷，應考慮使用其他資料結構。
  
在使用 WeakMap 時，確保你的設計考慮到了這些特性，特別是在數據管理和記憶體使用方面。

## 一句總結
WeakMap 是一種適合用於存儲物件鍵-值對的資料結構，具有弱引用特性，能有效管理記憶體。