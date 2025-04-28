<!--
Meta Description: # IDBKeyRange：JavaScript 中的索引資料庫鍵範圍 ## 概述 `IDBKeyRange` 是一個用於 IndexedDB 的 JavaScript 介面，專門用於定義一組鍵範圍，使得資料的查詢更加靈活和高效。它允許開發者在資料庫中進行範圍查詢，支持多種查詢模式。 ## 文件說明...
Meta Keywords: idbkeyrange, const, 100, javascript, lowerbound
-->

# IDBKeyRange：JavaScript 中的索引資料庫鍵範圍

## 概述
`IDBKeyRange` 是一個用於 IndexedDB 的 JavaScript 介面，專門用於定義一組鍵範圍，使得資料的查詢更加靈活和高效。它允許開發者在資料庫中進行範圍查詢，支持多種查詢模式。

## 文件說明
`IDBKeyRange` 的主要用途是生成可以用於查找資料的鍵範圍。此介面提供了靜態方法來創建不同類型的範圍，如單一鍵、包含範圍和不包含範圍。這些範圍可用於 `IDBObjectStore` 和 `IDBIndex` 的查詢操作。

### 主要方法
- **`IDBKeyRange.only(value)`**: 創建一個只包含指定值的鍵範圍。
- **`IDBKeyRange.lowerBound(lower, open)`**: 創建一個以指定的下邊界為起點的鍵範圍。
- **`IDBKeyRange.upperBound(upper, open)`**: 創建一個以指定的上邊界為終點的鍵範圍。
- **`IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)`**: 創建一個包含上下邊界的鍵範圍。

### 使用方式
使用 `IDBKeyRange` 時，開發者需首先創建一個鍵範圍，然後將其傳遞給查詢方法，例如 `IDBObjectStore.openCursor` 或 `IDBIndex.openCursor`。

## 範例
```javascript
// 創建一個 IDBKeyRange 物件，只包含值 42
const keyRange = IDBKeyRange.only(42);

// 使用 lowerBound 創建一個下邊界為 10 的範圍
const lowerBoundRange = IDBKeyRange.lowerBound(10);

// 使用 upperBound 創建一個上邊界為 100 的範圍
const upperBoundRange = IDBKeyRange.upperBound(100);

// 使用 bound 創建一個範圍，包含 10 到 100 的所有值
const boundRange = IDBKeyRange.bound(10, 100);
```

## 解釋
在使用 `IDBKeyRange` 時，開發者應注意以下幾點：
- 確保傳遞的值的類型與資料庫中存儲的鍵類型相符，以避免查詢失敗。
- `open` 參數決定了範圍是否包含邊界值，使用時需明確需求。
- 在查詢時，盡量使用索引來提高查詢效率，特別是在大型資料集上。

## 總結
`IDBKeyRange` 允許開發者靈活地定義鍵的範圍，從而在 IndexedDB 中進行高效的資料查詢。