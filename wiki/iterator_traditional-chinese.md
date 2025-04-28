<!--
Meta Description: # JavaScript 迭代器 (Iterator) 完全指南 ## 摘要 在 JavaScript 中，迭代器是一種對象，使得遍歷集合（如數組、字符串等）變得更加簡單和一致。通過迭代器，可以逐個訪問集合的元素，而無需關心集合的具體實現。 ## 文檔 ### 目的 迭代器的主要目的是提供一種統一的...
Meta Keywords: iterator, next, javascript, value, done
-->

# JavaScript 迭代器 (Iterator) 完全指南

## 摘要
在 JavaScript 中，迭代器是一種對象，使得遍歷集合（如數組、字符串等）變得更加簡單和一致。通過迭代器，可以逐個訪問集合的元素，而無需關心集合的具體實現。

## 文檔
### 目的
迭代器的主要目的是提供一種統一的方式來訪問集合中的元素，而不需要使用具體的索引或鍵。這樣的設計使得不同數據結構的遍歷變得簡單且一致。

### 使用方法
在 JavaScript 中，迭代器遵循一個特定的協定，即必須實現`next()`方法，該方法返回一個對象，包含兩個屬性：
- `value`：當前的元素值。
- `done`：一個布爾值，指示迭代器是否已經完成。

要使用迭代器，通常會調用集合的`Symbol.iterator`屬性，返回一個迭代器對象。這樣，我們就可以通過`next()`方法逐個獲取元素。

### 迭代器的實現
所有可迭代對象（如 Array、String、Map、Set 等）都實現了迭代器。用戶可以定義自定義的可迭代對象，通過實現`Symbol.iterator`方法來返回相應的迭代器。

## 範例
### 基本用法
以下是如何使用 JavaScript 的迭代器的基本範例：

```javascript
// 創建一個數組
const array = [1, 2, 3];

// 獲取數組的迭代器
const iterator = array[Symbol.iterator]();

// 使用迭代器訪問每個元素
console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### 自定義可迭代對象
下面的範例展示如何創建一個自定義的可迭代對象：

```javascript
const myIterable = {
  *[Symbol.iterator]() {
    yield 1;
    yield 2;
    yield 3;
  }
};

for (const value of myIterable) {
  console.log(value); // 1, 2, 3
}
```

## 解釋
### 常見陷阱
1. **未實現 `next()` 方法**：如果自定義對象未正確實現`next()`方法，將無法正常使用迭代器。
2. **忘記返回 `done` 屬性**：在返回的對象中，如果沒有正確設置`done`屬性，可能導致迭代過程中出現意外行為。

### 注意事項
- 迭代器是惰性求值的，這意味著只有在調用`next()`方法時，才會計算下一個值。
- 使用`for...of`循環時，自動使用迭代器進行遍歷，簡化了語法。

## 一句話總結
JavaScript 中的迭代器提供了一種一致的方式來遍歷集合，簡化了數據結構的操作。