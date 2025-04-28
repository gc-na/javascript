<!--
Meta Description: # URLSearchParams：JavaScript 中的 URL 參數處理工具 ## 摘要 `URLSearchParams` 是一個用於操作和處理 URL 查詢參數的 JavaScript 內建物件，提供了一種簡便的方式來讀取、修改和生成查詢字串。 ## 文檔 `URLSearchParam...
Meta Keywords: urlsearchparams, key1, params, url, key2
-->

# URLSearchParams：JavaScript 中的 URL 參數處理工具

## 摘要
`URLSearchParams` 是一個用於操作和處理 URL 查詢參數的 JavaScript 內建物件，提供了一種簡便的方式來讀取、修改和生成查詢字串。

## 文檔
`URLSearchParams` 物件允許開發者輕鬆地管理 URL 查詢字符串。查詢字符串是 URL 中以 `?` 開頭的部分，包含一組鍵值對，例如 `?key1=value1&key2=value2`。

### 目的
`URLSearchParams` 的主要目的是提供一個簡單的 API 來操作 URL 中的查詢參數，從而使得讀取和編輯這些參數變得更加直觀。

### 使用方法
首先，您可以使用 `new URLSearchParams()` 來創建一個新的 URLSearchParams 實例。這個實例可以接受一個查詢字符串或一個物件作為參數。

#### 語法：
```javascript
let params = new URLSearchParams(init);
```

#### 參數：
- `init`：可以是查詢字符串（如 `"?key1=value1&key2=value2"`）或一個物件（如 `{ key1: 'value1', key2: 'value2' }`）。

### 常用方法：
- `get(name)`：獲取指定參數的值。
- `set(name, value)`：設置指定參數的值。
- `append(name, value)`：添加一個新的參數值。
- `delete(name)`：刪除指定的參數。
- `has(name)`：檢查是否存在指定的參數。
- `toString()`：將所有參數轉換為查詢字符串格式。

## 範例
### 基本用法
```javascript
// 創建一個 URLSearchParams 實例
let params = new URLSearchParams('key1=value1&key2=value2');

// 獲取參數值
console.log(params.get('key1')); // 輸出：value1

// 設置參數值
params.set('key1', 'newValue');
console.log(params.toString()); // 輸出：key1=newValue&key2=value2

// 添加新參數
params.append('key3', 'value3');
console.log(params.toString()); // 輸出：key1=newValue&key2=value2&key3=value3

// 刪除參數
params.delete('key2');
console.log(params.toString()); // 輸出：key1=newValue&key3=value3
```

## 解釋
使用 `URLSearchParams` 時，開發者需要注意以下幾點：
1. **重複的鍵**：`URLSearchParams` 允許同一個鍵有多個值。使用 `get()` 方法時，只會返回第一個值，若要獲取所有值，需使用 `getAll()` 方法。
2. **編碼**：當添加或獲取參數時，需注意 URL 編碼。特殊字符需進行適當編碼。
3. **瀏覽器支持**：大多數現代瀏覽器均支持 `URLSearchParams`，但在使用之前，建議檢查目標瀏覽器的兼容性。

## 總結
`URLSearchParams` 是一個強大的工具，能夠簡化 URL 查詢參數的操作，提升開發效率。