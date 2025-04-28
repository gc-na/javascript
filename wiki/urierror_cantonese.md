<!--
Meta Description: # JavaScript URIError：理解與使用 ## 概要 URIError 是 JavaScript 中的一種錯誤類型，通常在 URI（統一資源標識符）相關的操作中發生錯誤時引發，例如使用 `decodeURI()` 或 `decodeURIComponent()` 函數時。 ## 文檔 ...
Meta Keywords: urierror, uri, javascript, decodeuricomponent, decodeuri
-->

# JavaScript URIError：理解與使用

## 概要
URIError 是 JavaScript 中的一種錯誤類型，通常在 URI（統一資源標識符）相關的操作中發生錯誤時引發，例如使用 `decodeURI()` 或 `decodeURIComponent()` 函數時。

## 文檔
### 目的
URIError 的主要目的是幫助開發者檢測和處理在 URI 編碼和解碼過程中出現的錯誤。當提供的 URI 字符串格式不正確時，會拋出此錯誤。

### 使用
在 JavaScript 中，URIError 主要用於以下兩個函數：
- `decodeURI()`
- `decodeURIComponent()`

這些函數用於解碼已經用 `encodeURI()` 或 `encodeURIComponent()` 編碼的 URI。如果解碼過程中遇到不正確的字符或格式，將會引發 URIError。

### 詳細信息
- **錯誤類型**：URIError 是內建的錯誤類型之一，繼承自 `Error` 類。
- **錯誤信息**：當 URIError 被拋出時，錯誤消息通常會提供有關錯誤的詳細描述，例如 "URI malformed"。

## 範例
以下是一些 URIError 的基本使用示例：

### 示例 1：使用 decodeURI()
```javascript
try {
    const result = decodeURI("http://example.com/%E4%BD%A0%E5%A5%BD");
    console.log(result); // 輸出: http://example.com/你好
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError:", e.message);
    }
}
```

### 示例 2：使用 decodeURIComponent()
```javascript
try {
    const result = decodeURIComponent("Hello%20World%21");
    console.log(result); // 輸出: Hello World!
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError:", e.message);
    }
}
```

### 示例 3：錯誤情況
```javascript
try {
    const result = decodeURIComponent("%E0%A4%A");
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError:", e.message); // 輸出: URIError: URI malformed
    }
}
```

## 解釋
在使用 URI 相關函數時，開發者需注意以下幾點：
- **格式正確性**：確保傳遞給 `decodeURI()` 和 `decodeURIComponent()` 的字符串格式正確，否則將引發 URIError。
- **錯誤處理**：使用 `try...catch` 塊來捕獲和處理 URIError，以避免應用程式崩潰。
- **字符編碼**：了解 URI 的字符編碼規則，尤其是在處理非 ASCII 字符時，以確保正確的編碼和解碼。

## 一句總結
URIError 是一種在 JavaScript 中處理 URI 編碼和解碼過程中出現的錯誤，通常由於格式不正確的 URI 字符串引起。