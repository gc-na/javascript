<!--
Meta Description: # JSON 在 JavaScript 中的應用與使用指南 ## 概要 JSON（JavaScript 物件標記法）是一種輕量級的資料交換格式，方便人類閱讀和編寫，同時也方便機器解析和生成。在 JavaScript 中，JSON 是廣泛使用的資料格式，特別是在與伺服器進行資料交互時。 ## 文件說明...
Meta Keywords: json, javascript, name, john, parse
-->

# JSON 在 JavaScript 中的應用與使用指南

## 概要
JSON（JavaScript 物件標記法）是一種輕量級的資料交換格式，方便人類閱讀和編寫，同時也方便機器解析和生成。在 JavaScript 中，JSON 是廣泛使用的資料格式，特別是在與伺服器進行資料交互時。

## 文件說明
### 目的
JSON 的主要目的是提供一種簡單的方式來表示結構化資料，特別是在 web 應用程式中進行資料傳輸時。它是 JavaScript 的一部分，可以直接用於 JavaScript 程式碼中。

### 使用方法
在 JavaScript 中，JSON 主要有以下兩個方法：
- `JSON.stringify(value)`：將 JavaScript 值轉換為 JSON 字串。
- `JSON.parse(text)`：將 JSON 字串轉換為 JavaScript 值。

### 詳細說明
1. **JSON.stringify(value)**：
   - 這個方法接受一個 JavaScript 值（物件或陣列），並返回一個 JSON 格式的字串。
   - 例如，`JSON.stringify({ name: "John", age: 30 })` 會返回 `'{"name":"John","age":30}'`。

2. **JSON.parse(text)**：
   - 此方法接受一個 JSON 格式的字串，並返回相應的 JavaScript 值。
   - 例如，`JSON.parse('{"name":"John","age":30}')` 會返回物件 `{ name: "John", age: 30 }`。

## 範例
### 使用 JSON.stringify
```javascript
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

const jsonString = JSON.stringify(person);
console.log(jsonString); // 輸出: {"name":"John","age":30,"city":"New York"}
```

### 使用 JSON.parse
```javascript
const jsonString = '{"name":"John","age":30,"city":"New York"}';
const person = JSON.parse(jsonString);
console.log(person.name); // 輸出: John
```

## 解釋
在使用 JSON 時，開發者常遇到一些常見的問題和注意事項：
- **資料型別限制**：JSON 支援的資料型別僅限於字串、數字、布林值、陣列、物件和 null。函式和未定義的值不能被 JSON 包含。
- **字串格式**：JSON 字串必須使用雙引號來包圍屬性名稱和字串值。
- **錯誤處理**：使用 `JSON.parse` 時，若傳入的字串無法解析為有效的 JSON，將導致錯誤，因此應使用 try-catch 進行錯誤處理。
    
```javascript
try {
    const obj = JSON.parse('{"name":"John", "age":30}');
    console.log(obj);
} catch (error) {
    console.error("JSON 解析錯誤:", error);
}
```

## 總結
JSON 是一種方便且廣泛使用的資料格式，在 JavaScript 中透過 `JSON.stringify` 和 `JSON.parse` 方法，能輕鬆地進行資料轉換和交互。