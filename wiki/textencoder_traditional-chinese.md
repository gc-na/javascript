<!--
Meta Description: # JavaScript 的 TextEncoder：編碼字符串的工具 ## 概述 `TextEncoder` 是一個用於將 JavaScript 字符串編碼為 `Uint8Array` 的內建對象，主要用於處理文本數據的編碼，特別是在 Web API 和二進制數據交互時非常有用。 ## 文檔 ##...
Meta Keywords: textencoder, const, encoder, javascript, uint8array
-->

# JavaScript 的 TextEncoder：編碼字符串的工具

## 概述
`TextEncoder` 是一個用於將 JavaScript 字符串編碼為 `Uint8Array` 的內建對象，主要用於處理文本數據的編碼，特別是在 Web API 和二進制數據交互時非常有用。

## 文檔
### 目的
`TextEncoder` 的主要目的是提供一種將 UTF-8 編碼字符串轉換為字節數組的方式，這在處理網絡請求、文件處理或其他需要字節格式的場合中非常重要。

### 使用方法
`TextEncoder` 的基本使用方式如下：

```javascript
const encoder = new TextEncoder();
const encodedData = encoder.encode("Hello, World!");
```

#### 參數
- `TextEncoder` 的構造函數可以接受一個可選的 `label` 參數，用於指定編碼格式（默認為 "utf-8"）。

### 返回值
`encode()` 方法返回一個 `Uint8Array`，其中包含了編碼後的字節數據。

## 示例
以下是 `TextEncoder` 的基本用法示例：

### 示例 1：基本編碼
```javascript
const encoder = new TextEncoder();
const encoded = encoder.encode("你好，世界！");
console.log(encoded); // Uint8Array(15) [ 228, 189, 160, 229, 165, 189, 232, 191, 160, 229, 164, 167, 229, 174, 154 ]
```

### 示例 2：自定義編碼
```javascript
const encoder = new TextEncoder("utf-16");
const encoded = encoder.encode("Hello, World!");
console.log(encoded); // Uint8Array(26) [ 72, 0, 101, 0, 108, 0, 108, 0, 111, 0, 44, 0, 32, 0, 87, 0, 111, 0, 114, 0, 108, 0, 100, 0, 33, 0 ]
```

## 解釋
### 常見陷阱
1. **編碼格式**：`TextEncoder` 默認使用 UTF-8 編碼，若需要使用其他編碼格式（如 UTF-16），需要在創建 `TextEncoder` 實例時明確指定。
2. **處理空字符串**：對於空字符串，`encode()` 方法會返回一個空的 `Uint8Array`，這可能會導致某些後續操作出錯。

### 附加說明
- `TextEncoder` 通常用於網絡請求的數據傳輸，例如，當需要將字符串數據轉換為可以通過 Fetch API 發送的格式時。
- `TextEncoder` 只能處理字符串數據，對於其他數據類型（如數字或對象），需要先轉換為字符串。

## 總結
`TextEncoder` 是一個強大的工具，能夠有效地將文本字符串轉換為字節數組，對於需要編碼和數據傳輸的場景至關重要。