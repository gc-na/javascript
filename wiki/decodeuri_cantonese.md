<!--
Meta Description: # 使用 decodeURI 的 JavaScript 解碼工具 ## 簡介 `decodeURI` 是 JavaScript 中的一個內建函數，用於解碼經過編碼的 Uniform Resource Identifier (URI)。當 URI 中包含特殊字符時，這些字符會被編碼成特定格式，以便於在...
Meta Keywords: uri, decodeuri, javascript, encodeduri, const
-->

# 使用 decodeURI 的 JavaScript 解碼工具

## 簡介
`decodeURI` 是 JavaScript 中的一個內建函數，用於解碼經過編碼的 Uniform Resource Identifier (URI)。當 URI 中包含特殊字符時，這些字符會被編碼成特定格式，以便於在 URL 中安全傳輸。

## 文檔
### 目的
`decodeURI` 函數的主要目的是將經過 `encodeURI` 編碼的 URI 字符串轉換回原始字符串。這對於處理傳遞參數或路徑中的特殊字符特別重要。

### 使用方法
```javascript
decodeURI(encodedURI)
```
- **參數**:
  - `encodedURI` (String): 一個經過編碼的 URI 字符串，包含 `%` 符號及其後面的十六進制數字表示的字符。

- **返回值**:
  - 返回一個解碼後的字符串。

### 詳細說明
- `decodeURI` 不會解碼所有的字符，特別是那些在 URI 中具有特殊意義的字符，例如 `#`、`?`、`&` 等。這是因為這些字符在 URL 中用於分隔不同的部分，解碼後可能會導致無法正確解析。
- `decodeURI` 主要用於處理整個 URI，而不是 URI 的查詢參數。

## 範例
### 基本用法
```javascript
const encodedURI = "https%3A%2F%2Fwww.example.com%2Fhello%3Fname%3DJohn%26age%3D30";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 輸出: "https://www.example.com/hello?name=John&age=30"
```

### 處理特殊字符
```javascript
const encodedURI = "城市%20與%20國家%20%28City%20and%20Country%29";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 輸出: "城市與國家（City and Country）"
```

## 解釋
- **常見陷阱**: 使用 `decodeURI` 時，請注意不能解碼包含特殊字符的部分。例如：
  ```javascript
  const uri = "https://www.example.com/test#section";
  const decodedURI = decodeURI(uri);
  console.log(decodedURI); // 輸出: "https://www.example.com/test#section" (不會解碼 #)
  ```

- **與 decodeURIComponent 的區別**: `decodeURIComponent` 函數能夠解碼 URI 組件，這意味著它會解碼所有的字符，包括那些在 URI 中具有特殊意義的字符。選擇使用哪個函數取決於你的需求。

## 一句總結
`decodeURI` 是一個用於解碼經過編碼的 URI 字符串的 JavaScript 函數，能夠將 `%` 符號及其後的十六進制數字轉換回原始字符。