<!--
Meta Description: # JavaScript 迭代器（Iterator）詳解 ## 簡介 JavaScript 的迭代器是一種對象，提供了一種統一的方式來遍歷集合（如陣列、物件等）的元素。透過迭代器，我們可以逐個訪問集合中的項目，而不需要直接操作集合的內部結構。 ## 文檔 ### 目的 迭代器的主要目的是提供一種標準...
Meta Keywords: done, iterator, next, value, javascript
-->

# JavaScript 迭代器（Iterator）詳解

## 簡介
JavaScript 的迭代器是一種對象，提供了一種統一的方式來遍歷集合（如陣列、物件等）的元素。透過迭代器，我們可以逐個訪問集合中的項目，而不需要直接操作集合的內部結構。

## 文檔
### 目的
迭代器的主要目的是提供一種標準的方式來遍歷資料結構。它遵循特定的協議，使得不同的資料結構可以使用相同的方式進行遍歷。

### 使用方法
在 JavaScript 中，迭代器通常會實現 `next()` 方法，該方法返回一個對象，該對象包含兩個屬性：
- `value`：當前元素的值。
- `done`：布林值，指示是否已經遍歷完所有元素。

要創建自定義的迭代器，對象需要實現 `Symbol.iterator` 方法，該方法返回一個迭代器對象。

### 詳細說明
以下是使用迭代器的基本步驟：
1. 實現 `Symbol.iterator` 方法。
2. 在該方法中返回一個擁有 `next()` 方法的對象。
3. `next()` 方法返回一個含有 `value` 和 `done` 的對象。

以下是一個簡單的例子：

```javascript
const myIterable = {
  data: [1, 2, 3],
  [Symbol.iterator]() {
    let index = 0;
    return {
      next: () => {
        if (index < this.data.length) {
          return { value: this.data[index++], done: false };
        } else {
          return { done: true };
        }
      }
    };
  }
};
```

## 範例
### 基本用法
使用迭代器遍歷一個陣列的範例：

```javascript
const array = [1, 2, 3];
const iterator = array[Symbol.iterator]();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { done: true }
```

### 自定義迭代器
下面是自定義迭代器的範例：

```javascript
const myIterable = {
  data: ['a', 'b', 'c'],
  [Symbol.iterator]() {
    let index = 0;
    return {
      next: () => {
        if (index < this.data.length) {
          return { value: this.data[index++], done: false };
        } else {
          return { done: true };
        }
      }
    };
  }
};

for (let value of myIterable) {
  console.log(value); // 輸出：a, b, c
}
```

## 解釋
### 常見陷阱
- 在使用迭代器時，確保 `next()` 方法始終返回包含 `value` 和 `done` 的對象。
- 確保 `done` 屬性在所有元素遍歷完成後返回 `true`，以避免無窮迴圈。

### 注意事項
- 迭代器可以與 `for...of` 循環結合使用，這提供了一種簡潔的語法來遍歷集合。
- 理解迭代器的協議對於實現自定義集合的遍歷至關重要。

## 總結
JavaScript 的迭代器提供了一種靈活且標準化的方式來遍歷資料結構，使得開發者能夠輕鬆地訪問集合中的元素。