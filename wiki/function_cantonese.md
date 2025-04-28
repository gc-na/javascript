<!--
Meta Description: # JavaScript 函數 (Function) 詳細指南 ## 簡介 JavaScript 函數是一段可重用的代碼，能夠執行特定任務或計算。它們是 JavaScript 的核心概念，能夠幫助開發者組織和管理程式碼。 ## 文檔 ### 目的 函數的主要目的是封裝邏輯以便重用。透過定義函數，開發...
Meta Keywords: javascript, function, return, const, 函數名稱
-->

# JavaScript 函數 (Function) 詳細指南

## 簡介
JavaScript 函數是一段可重用的代碼，能夠執行特定任務或計算。它們是 JavaScript 的核心概念，能夠幫助開發者組織和管理程式碼。

## 文檔
### 目的
函數的主要目的是封裝邏輯以便重用。透過定義函數，開發者可以簡化代碼結構，提升可讀性和維護性。

### 使用方法
函數可以通過以下方式定義：
1. 函數聲明（Function Declaration）
2. 函數表達式（Function Expression）
3. 箭頭函數（Arrow Function）

### 主要細節
- **函數聲明**：
  ```javascript
  function 函數名稱(參數1, 參數2) {
      // 函數主體
      return 回傳值;
  }
  ```

- **函數表達式**：
  ```javascript
  const 函數名稱 = function(參數1, 參數2) {
      // 函數主體
      return 回傳值;
  };
  ```

- **箭頭函數**：
  ```javascript
  const 函數名稱 = (參數1, 參數2) => {
      // 函數主體
      return 回傳值;
  };
  ```

函數可以接受任何數量的參數，並且可以返回一個值。若無返回值，則預設返回 `undefined`。

## 示例
### 基本用法
1. 函數聲明示例：
   ```javascript
   function 加法(a, b) {
       return a + b;
   }
   console.log(加法(5, 3)); // 輸出: 8
   ```

2. 函數表達式示例：
   ```javascript
   const 減法 = function(a, b) {
       return a - b;
   };
   console.log(減法(5, 3)); // 輸出: 2
   ```

3. 箭頭函數示例：
   ```javascript
   const 乘法 = (a, b) => a * b;
   console.log(乘法(5, 3)); // 輸出: 15
   ```

## 解釋
### 常見陷阱
- **作用域問題**：函數內部的變數無法在外部訪問，這可能會造成混淆。
- **this 關鍵字**：在不同的上下文中，`this` 的指向會有所不同。箭頭函數不會創建自己的 `this`，而是從外部上下文繼承。
- **未定義的參數**：如果調用函數時未提供所有參數，未提供的參數將是 `undefined`。

## 總結
JavaScript 函數是一個強大的工具，能夠幫助開發者創建可重用且高效的代碼結構。