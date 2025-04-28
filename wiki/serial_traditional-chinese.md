<!--
Meta Description: # JavaScript 中的序列化 (Serial) ## 概述 在 JavaScript 中，序列化是將 JavaScript 對象轉換為可存儲或傳輸的格式的過程。這通常涉及將對象轉換為 JSON 字符串，以便於網絡傳輸或在本地存儲。 ## 文檔 序列化的主要目的在於將複雜的數據結構（如對象和數...
Meta Keywords: json, javascript, const, obj, name
-->

# JavaScript 中的序列化 (Serial)

## 概述
在 JavaScript 中，序列化是將 JavaScript 對象轉換為可存儲或傳輸的格式的過程。這通常涉及將對象轉換為 JSON 字符串，以便於網絡傳輸或在本地存儲。

## 文檔
序列化的主要目的在於將複雜的數據結構（如對象和數組）轉換為字符串，從而便於存儲或在網絡上傳輸。JavaScript 提供了 `JSON.stringify()` 方法來實現序列化，而相對應的 `JSON.parse()` 方法則用於反序列化。

### 用法
- **序列化**：使用 `JSON.stringify()` 將 JavaScript 對象轉換為 JSON 字符串。
- **反序列化**：使用 `JSON.parse()` 將 JSON 字符串轉換回 JavaScript 對象。

### 詳細說明
- `JSON.stringify(value[, replacer[, space]])`
  - `value`：要序列化的 JavaScript 值（通常為對象或數組）。
  - `replacer`：（可選）可以是一個函數或數組，用於選擇性地包含或排除某些值。
  - `space`：（可選）用於美化輸出的空格數量。

- `JSON.parse(text[, reviver])`
  - `text`：要反序列化的 JSON 字符串。
  - `reviver`：（可選）可以是一個函數，用於在解析每個鍵值時進行轉換。

## 範例
### 序列化範例
```javascript
const obj = { name: "Alice", age: 30, city: "Taipei" };
const jsonString = JSON.stringify(obj);
console.log(jsonString); // 輸出：{"name":"Alice","age":30,"city":"Taipei"}
```

### 反序列化範例
```javascript
const jsonString = '{"name":"Alice","age":30,"city":"Taipei"}';
const obj = JSON.parse(jsonString);
console.log(obj.name); // 輸出：Alice
```

### 使用 replacer 和 space
```javascript
const obj = { name: "Alice", age: 30, city: "Taipei" };
const jsonString = JSON.stringify(obj, null, 2);
console.log(jsonString);
/* 輸出：
{
  "name": "Alice",
  "age": 30,
  "city": "Taipei"
}
*/
```

## 解釋
在序列化過程中，某些數據類型（例如函數、undefined 和 Symbol）將無法被序列化。這可能會導致意外的行為或錯誤。此外，對象的循環引用也會引發錯誤。在使用 `JSON.parse()` 時，必須確保字符串格式正確，否則會拋出錯誤。

## 一句總結
序列化是將 JavaScript 對象轉換為 JSON 字符串的過程，方便存儲和傳輸數據。