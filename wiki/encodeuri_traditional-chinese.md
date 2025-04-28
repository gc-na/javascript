<!--
Meta Description: # 在JavaScript中使用encodeURI函數的詳細指南 ## 摘要 `encodeURI` 是一個JavaScript全局函數，用於編碼URI（統一資源標識符），以確保其在網絡傳輸過程中不會被誤解。 ## 文檔 ### 目的 `encodeURI` 函數的主要目的是將URI中的特殊字符編碼...
Meta Keywords: encodeuri, uri, let, https, example
-->

# 在JavaScript中使用encodeURI函數的詳細指南

## 摘要
`encodeURI` 是一個JavaScript全局函數，用於編碼URI（統一資源標識符），以確保其在網絡傳輸過程中不會被誤解。

## 文檔
### 目的
`encodeURI` 函數的主要目的是將URI中的特殊字符編碼，這樣可以確保網址在傳輸過程中不會被錯誤解讀，特別是在包含空格、特殊符號等情況下。

### 用法
```javascript
encodeURI(uri)
```
- **參數**:
  - `uri` (String): 需要編碼的URI字符串。
- **返回值**: 返回編碼後的URI字符串，其中某些字符被替換為百分比編碼（percent-encoded）格式。

### 詳細說明
`encodeURI` 不會編碼整個URI，而是會保留某些字符，例如：冒號（:）、斜線（/）、問號（?）、井號（#）等，因為這些字符在URI中具有特殊意義。使用這個函數時應注意其行為與 `encodeURIComponent` 的不同，後者會對所有字符進行編碼，包括那些在URI中有特殊含義的字符。

## 範例
### 基本用法
```javascript
let uri = "https://example.com/search?query=hello world";
let encodedUri = encodeURI(uri);
console.log(encodedUri); // 輸出: "https://example.com/search?query=hello%20world"
```

### 包含特殊字符的範例
```javascript
let uriWithSpecialChars = "https://example.com/test?param=100%&$#@!";
let encodedUriWithSpecialChars = encodeURI(uriWithSpecialChars);
console.log(encodedUriWithSpecialChars); // 輸出: "https://example.com/test?param=100%&$#@!"
```

## 解釋
### 常見陷阱及注意事項
1. **不編碼特殊字符**: `encodeURI` 不會編碼某些字符，如`?`和`&`，這可能會導致在查詢字符串中出現意外行為。
2. **與 `encodeURIComponent` 的區別**: 如果需要對URI的某個部分進行全面編碼，建議使用 `encodeURIComponent`，因為它會編碼所有的特殊字符，包括那些在URI中有特殊意義的字符。
3. **URL的長度限制**: 雖然 `encodeURI` 可以編碼URI，但過長的URL可能會超過瀏覽器或伺服器的限制，因此需要注意編碼後的長度。

## 一句總結
`encodeURI` 是一個用於將URI進行編碼的JavaScript函數，能夠保護URI在網絡傳輸過程中的完整性。