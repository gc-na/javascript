<!--
Meta Description: # JSON 在 JavaScript 中的應用與使用 ## 概述 JSON（JavaScript Object Notation）是一種輕量級的數據交換格式，易於人類閱讀和編寫，也易於機器解析和生成。它基於 JavaScript 的語法，但已成為獨立於語言的數據格式，廣泛應用於Web應用程序中。 ...
Meta Keywords: json, javascript, stringify, parse, const
-->

# JSON 在 JavaScript 中的應用與使用

## 概述
JSON（JavaScript Object Notation）是一種輕量級的數據交換格式，易於人類閱讀和編寫，也易於機器解析和生成。它基於 JavaScript 的語法，但已成為獨立於語言的數據格式，廣泛應用於Web應用程序中。

## 文檔
### 目的
JSON 用於表示結構化數據，特別是在客戶端和伺服器之間交換數據時。它的簡單性和可讀性使其成為許多應用程序的首選數據格式。

### 使用方法
在 JavaScript 中，JSON 提供了兩個主要的方法：
- `JSON.stringify(value[, replacer[, space]])`：將 JavaScript 值（如對象或數組）轉換為 JSON 字符串。
- `JSON.parse(text[, reviver])`：將 JSON 字符串轉換為 JavaScript 對象。

### 詳細資訊
- **JSON.stringify**：可以選擇性地使用 `replacer` 參數來過濾或改變結果，並使用 `space` 參數來美化輸出。
- **JSON.parse**：可以使用 `reviver` 參數來對解析過程中的每個鍵值對進行轉換。

## 範例
### 基本用法示例
```javascript
// 將對象轉換為 JSON 字符串
const obj = { name: "小明", age: 25 };
const jsonString = JSON.stringify(obj);
console.log(jsonString); // 輸出: {"name":"小明","age":25}

// 將 JSON 字符串轉換為對象
const jsonString = '{"name":"小明","age":25}';
const parsedObj = JSON.parse(jsonString);
console.log(parsedObj.name); // 輸出: 小明
```

## 解釋
在使用 JSON 時，開發者需要注意以下幾點：
- JSON 的鍵必須是字符串，並且必須用雙引號包圍。
- JSON 不能包含函數、日期對象或未定義的值。
- 在解析 JSON 字符串時，若字符串格式不正確，將引發錯誤。

## 總結
JSON 是一種用於數據交換的輕量級格式，在 JavaScript 中使用 `JSON.stringify` 和 `JSON.parse` 進行數據處理。