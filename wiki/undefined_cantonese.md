<!--
Meta Description: # JavaScript 中的 "undefined": 完整指南 ## 摘要 在 JavaScript 中，`undefined` 是一個基本類型，表示變數已被宣告，但尚未賦值。這是 JavaScript 中用來表示不存在或未定義的值。 ## 文檔 ### 目的 `undefined` 在 Jav...
Meta Keywords: undefined, javascript, console, log, null
-->

# JavaScript 中的 "undefined": 完整指南

## 摘要
在 JavaScript 中，`undefined` 是一個基本類型，表示變數已被宣告，但尚未賦值。這是 JavaScript 中用來表示不存在或未定義的值。

## 文檔
### 目的
`undefined` 在 JavaScript 中是自動賦值給未初始化的變數。當一個變數被宣告但沒有被賦予值時，其值將為 `undefined`。

### 使用方法
- 當創建變數但不初始化時：
  ```javascript
  let myVar;
  console.log(myVar); // 輸出: undefined
  ```

- 當函數沒有返回值時：
  ```javascript
  function myFunction() {}
  console.log(myFunction()); // 輸出: undefined
  ```

- 當訪問不存在的對象屬性時：
  ```javascript
  let obj = {};
  console.log(obj.nonExistentProperty); // 輸出: undefined
  ```

### 詳細說明
在 JavaScript 中，`undefined` 是一個原始數據類型，與 `null` 不同。雖然它們都表示“無值”，但 `undefined` 表示變數尚未被賦值，而 `null` 通常是有意識地賦予變數的“空”值。

## 示例
1. 未初始化的變數：
   ```javascript
   let a;
   console.log(a); // 輸出: undefined
   ```

2. 函數返回值：
   ```javascript
   function example() {
     // 沒有 return 語句
   }
   console.log(example()); // 輸出: undefined
   ```

3. 物件屬性不存在：
   ```javascript
   const car = { brand: 'Toyota' };
   console.log(car.model); // 輸出: undefined
   ```

## 解釋
1. **常見陷阱**：有時，開發者可能會將 `undefined` 與 `null` 混淆。要記住，`undefined` 是由 JavaScript 自動生成的，而 `null` 是由開發者明確設置的。
   
2. **數據類型檢查**：使用 `typeof` 操作符來檢查變數是否為 `undefined`：
   ```javascript
   let b;
   console.log(typeof b === 'undefined'); // 輸出: true
   ```

3. **與其他類型的比較**：在進行比較時，`undefined` 與 `null` 和其他類型有不同的行為：
   ```javascript
   console.log(undefined == null); // 輸出: true
   console.log(undefined === null); // 輸出: false
   ```

## 一句總結
`undefined` 是 JavaScript 中表示變數未初始化或不存在的基本類型。