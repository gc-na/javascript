<!--
Meta Description: # IDBKeyRange: JavaScript 中的 IndexedDB 鍵範圍 ## 簡介 IDBKeyRange 是一個用於 IndexedDB 的 JavaScript 物件，提供了一個簡單的方法來定義一個鍵範圍，以便於查詢和過濾資料。 ## 文檔 IDBKeyRange 主要用於 Ind...
Meta Keywords: idbkeyrange, javascript, indexeddb, 的範圍, let
-->

# IDBKeyRange: JavaScript 中的 IndexedDB 鍵範圍

## 簡介
IDBKeyRange 是一個用於 IndexedDB 的 JavaScript 物件，提供了一個簡單的方法來定義一個鍵範圍，以便於查詢和過濾資料。

## 文檔
IDBKeyRange 主要用於 IndexedDB 的查詢過程中。它可以定義一組鍵值的範圍，並且支持多種查詢方式，包括開放、封閉及部分開放的範圍。這讓開發者能夠靈活地選擇所需的資料。

### 目的
在需要查詢一組鍵值時，IDBKeyRange 允許開發者定義特定的範圍來過濾資料，從而提高查詢效率。

### 用法
IDBKeyRange 有幾種靜態方法可用來創建鍵範圍：

1. **IDBKeyRange.only(key)**: 創建一個只包含特定鍵的範圍。
2. **IDBKeyRange.lowerBound(lower, open)**: 創建一個以指定鍵為下限的範圍，選擇性地設定下限是否開放。
3. **IDBKeyRange.upperBound(upper, open)**: 創建一個以指定鍵為上限的範圍，選擇性地設定上限是否開放。
4. **IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)**: 創建一個由下限和上限定義的範圍，可選擇設定下限和上限是否開放。

## 範例
以下是 IDBKeyRange 的基本用法範例：

```javascript
// 創建一個只包含鍵值 5 的範圍
let keyRange1 = IDBKeyRange.only(5);

// 創建一個下限為 10 的範圍
let keyRange2 = IDBKeyRange.lowerBound(10);

// 創建一個上限為 20 的範圍
let keyRange3 = IDBKeyRange.upperBound(20, true); // 上限為開放範圍

// 創建一個下限為 5，上限為 15 的範圍
let keyRange4 = IDBKeyRange.bound(5, 15, false, true); // 下限封閉，上限開放
```

## 解釋
在使用 IDBKeyRange 時，開發者需要注意以下幾點：

- 鍵值類型：IDBKeyRange 支持多種鍵值類型，包括數字、字串和日期，但必須確保用於範圍的鍵值類型一致。
- 開放與封閉範圍：開放範圍（`open`）意味著範圍的邊界不包括該邊界的鍵值，封閉範圍則相反。這在設計查詢時需要特別留意。
- 查詢性能：合理使用 IDBKeyRange 可以大幅提升資料查詢的性能，特別是在處理大量資料時。

## 一句總結
IDBKeyRange 是用於定義 IndexedDB 鍵範圍的 JavaScript 物件，提供靈活的查詢選項以增強資料操作的效率。