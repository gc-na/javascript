<!--
Meta Description: # JavaScript 的 WeakSet：用法及示例 ## 簡介 WeakSet 是 JavaScript 中的一種集合類型，它允許儲存對物件的弱引用。這意味著如果物件不再被引用，則可以被垃圾回收，從而有效地管理內存。 ## 文檔 ### 目的 WeakSet 主要用於儲存物件，並且不會阻止這些...
Meta Keywords: weakset, obj1, javascript, let, has
-->

# JavaScript 的 WeakSet：用法及示例

## 簡介
WeakSet 是 JavaScript 中的一種集合類型，它允許儲存對物件的弱引用。這意味著如果物件不再被引用，則可以被垃圾回收，從而有效地管理內存。

## 文檔
### 目的
WeakSet 主要用於儲存物件，並且不會阻止這些物件被垃圾回收。這使得 WeakSet 特別適合用於臨時儲存物件，或者在需要跟蹤物件的存在性但又不想影響其生命週期的情況下使用。

### 用法
WeakSet 的基本語法如下：

```javascript
let myWeakSet = new WeakSet([iterable]);
```

- `iterable`（選擇性）：一個可迭代對象，用於初始化 WeakSet。

### 方法
WeakSet 提供了以下三個方法：
- `add(value)`：將指定的物件添加到 WeakSet 中。
- `delete(value)`：從 WeakSet 中移除指定的物件。
- `has(value)`：檢查 WeakSet 是否包含指定的物件。

### 特點
- WeakSet 只能儲存對物件的弱引用，不能儲存原始類型的值（如數字、字符串等）。
- WeakSet 不支持迭代，因此無法使用 `forEach` 或 `for...of`。
- WeakSet 的大小無法直接獲取。

## 示例
以下是一些基本的 WeakSet 用法示例：

```javascript
// 創建一個 WeakSet
let obj1 = { name: "物件1" };
let obj2 = { name: "物件2" };
let weakset = new WeakSet([obj1]);

// 添加物件
weakset.add(obj2);

// 檢查物件是否存在
console.log(weakset.has(obj1)); // 輸出: true
console.log(weakset.has(obj2)); // 輸出: true

// 刪除物件
weakset.delete(obj1);
console.log(weakset.has(obj1)); // 輸出: false
```

## 解釋
### 常見陷阱及注意事項
- **物件的引用**：WeakSet 中的物件必須是引用類型，如果嘗試將原始類型的值添加到 WeakSet，將會拋出錯誤。
- **垃圾回收**：如果 WeakSet 中的物件沒有其他引用，這些物件會被垃圾回收，因此無法保證 WeakSet 的內容長期存在。
- **無法迭代**：WeakSet 不支持迭代，這意味著無法使用常見的迭代方法來檢索其內容。

## 一句總結
WeakSet 是一種允許儲存對物件的弱引用的集合，適合用於需要臨時跟蹤物件的場景。