<!--
Meta Description: # structuredClone：JavaScript 中的結構化複製方法 ## 摘要 `structuredClone` 是一個 JavaScript 原生方法，用於創建對象的深層複製，支援複製包括日期、地圖、集合等複雜數據類型，並且保留原始對象的結構和屬性。 ## 文檔 ### 目的 `str...
Meta Keywords: structuredclone, javascript, const, originalobject, clonedobject
-->

# structuredClone：JavaScript 中的結構化複製方法

## 摘要
`structuredClone` 是一個 JavaScript 原生方法，用於創建對象的深層複製，支援複製包括日期、地圖、集合等複雜數據類型，並且保留原始對象的結構和屬性。

## 文檔
### 目的
`structuredClone` 方法的主要目的是提供一種簡便的方式來深層複製對象，避免傳統複製方法（如 `JSON.parse(JSON.stringify(obj))`）的局限性，特別是在處理非基本數據類型時。

### 使用方法
`structuredClone` 的基本語法如下：

```javascript
const clonedObject = structuredClone(originalObject);
```

### 參數
- `originalObject`：需要被複製的原始對象。

### 返回值
返回一個新的對象，該對象是原始對象的深層複製。

### 特點
- 支援多種數據類型，包括：
  - 基本數據類型（如數字、字符串、布爾值）
  - 複雜數據類型（如對象、數組、日期、地圖、集合）
  - 其他特殊對象（如 `ArrayBuffer`、`TypedArray`）
- 會保留原始對象的結構，並且不會影響原始對象的參考。

## 示例
### 基本用法
```javascript
const originalObject = {
  name: "Alice",
  age: 30,
  dateOfBirth: new Date('1993-01-01'),
  hobbies: ['reading', 'traveling']
};

const clonedObject = structuredClone(originalObject);

console.log(clonedObject); // { name: "Alice", age: 30, dateOfBirth: Date, hobbies: ['reading', 'traveling'] }
```

### 複製集合
```javascript
const originalSet = new Set([1, 2, 3]);
const clonedSet = structuredClone(originalSet);

console.log(clonedSet); // Set { 1, 2, 3 }
```

### 複製地圖
```javascript
const originalMap = new Map([[1, 'one'], [2, 'two']]);
const clonedMap = structuredClone(originalMap);

console.log(clonedMap); // Map { 1 => 'one', 2 => 'two' }
```

## 解釋
### 常見陷阱
1. **循環引用**：`structuredClone` 能夠處理循環引用的對象，這是其相對於其他複製方法的一個優勢。
2. **無法複製函數**：使用 `structuredClone` 時，函數和某些特殊對象（如 DOM 元素）無法被複製，這一點需要注意。

### 額外說明
- `structuredClone` 是一個同步操作，複製大型對象時可能會影響性能。
- 在實際使用中，建議先檢查目標環境是否支援 `structuredClone`，因為某些舊版瀏覽器可能不支持該方法。

## 總結
`structuredClone` 是一個強大的 JavaScript 方法，可用於深層複製對象，特別是在需要處理複雜數據類型時，提供了一個高效且簡單的解決方案。