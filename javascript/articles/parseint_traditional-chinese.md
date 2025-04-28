<!--
Meta Description: # JavaScript 的 parseInt 函數詳解與使用指南 ## 簡介 `parseInt` 是 JavaScript 中一個用於將字符串轉換為整數的全局函數。此函數可以解析不同進制的數字並返回相應的整數值。 ## 文件說明 ### 功能 `parseInt` 函數的主要用途是將字符串轉換為...
Meta Keywords: parseint, javascript, console, log, string
-->

# JavaScript 的 parseInt 函數詳解與使用指南

## 簡介
`parseInt` 是 JavaScript 中一個用於將字符串轉換為整數的全局函數。此函數可以解析不同進制的數字並返回相應的整數值。

## 文件說明
### 功能
`parseInt` 函數的主要用途是將字符串轉換為整數。它支持從指定的進制（基數）解析數字，使得開發者可以靈活處理不同格式的數據。

### 語法
```javascript
parseInt(string, radix);
```

### 參數
- **string**: 要解析的字符串。若該字符串不能解析為數字，則返回 `NaN`（不是一個數字）。
- **radix**: 可選參數，指定要解析的進制（2 到 36 之間的整數）。若未提供，則根據字符串的格式自動推斷進制。

### 詳細說明
- 如果 `string` 以空格開始，這些空格將被忽略。
- 解析將從 `string` 的第一個字符開始，直到遇到無法解析的字符為止。
- 若 `radix` 為 0，則根據字符串的格式自動選擇進制：如果字符串以 "0x" 或 "0X" 開頭，則為 16 進制；如果以 "0" 開頭，則為 8 進制；否則為 10 進制。

## 範例
### 基本用法
```javascript
console.log(parseInt("123"));      // 輸出: 123
console.log(parseInt("1010", 2));  // 輸出: 10 (二進制轉十進制)
console.log(parseInt("0xF", 16));   // 輸出: 15 (十六進制轉十進制)
```

### 自動推斷進制
```javascript
console.log(parseInt("0123"));     // 輸出: 123 (十進制)
console.log(parseInt("0x1A"));     // 輸出: 26 (十六進制)
```

## 解釋
### 常見陷阱
- **返回 NaN**: 當 `string` 不是有效的數字格式時，`parseInt` 將返回 `NaN`。
  ```javascript
  console.log(parseInt("abc"));  // 輸出: NaN
  ```

- **進制影響**: 如果不明確指定 `radix`，可能會導致意想不到的結果。
  ```javascript
  console.log(parseInt("08"));   // 輸出: 8 (十進制)
  console.log(parseInt("010"));  // 輸出: 10 (十進制)
  ```

- **字串中包含非數字字符**: 解析過程將在遇到非數字字符時停止。
  ```javascript
  console.log(parseInt("123abc")); // 輸出: 123
  ```

### 額外注意事項
- `parseInt` 不會自動四捨五入，僅返回整數部分。
- 使用 `Number.isNaN()` 來檢查返回值是否為 `NaN`。

## 一句總結
`parseInt` 是一個用於將字符串轉換為整數的 JavaScript 函數，支持指定進制解析。