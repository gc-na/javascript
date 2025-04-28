<!--
Meta Description: # JavaScript 中的日期 (Date) 對象 ## 概要 JavaScript 的 Date 對象用於處理和操作日期和時間。它提供了多種方法來獲取當前日期、時間以及進行日期計算。 ## 文檔 ### 目的 Date 對象的主要目的是提供一種方法來創建、操作和格式化日期和時間。它支持多種日期...
Meta Keywords: date, javascript, const, now, console
-->

# JavaScript 中的日期 (Date) 對象

## 概要
JavaScript 的 Date 對象用於處理和操作日期和時間。它提供了多種方法來獲取當前日期、時間以及進行日期計算。

## 文檔
### 目的
Date 對象的主要目的是提供一種方法來創建、操作和格式化日期和時間。它支持多種日期格式和時間計算功能，使開發者能夠方便地處理時間相關的數據。

### 使用方法
要使用 Date 對象，只需創建一個新的 Date 實例：

```javascript
const currentDate = new Date();
```

這將創建一個包含當前日期和時間的 Date 對象。你也可以傳遞特定的日期和時間參數：

```javascript
const specificDate = new Date(2023, 9, 15); // 2023年10月15日
```

### 詳細信息
Date 對象的主要方法包括：
- `getFullYear()`: 獲取四位數的年份。
- `getMonth()`: 獲取月份（0-11，0表示一月）。
- `getDate()`: 獲取當月的日期（1-31）。
- `getHours()`: 獲取小時（0-23）。
- `getMinutes()`: 獲取分鐘（0-59）。
- `getSeconds()`: 獲取秒（0-59）。
- `getMilliseconds()`: 獲取毫秒（0-999）。
- `toISOString()`: 將 Date 對象轉換為 ISO 格式的字符串。

## 範例
### 基本使用範例
```javascript
// 獲取當前日期和時間
const now = new Date();
console.log(now);

// 獲取年份
const year = now.getFullYear();
console.log("年份:", year);

// 獲取月份
const month = now.getMonth() + 1; // 加1以獲取正確的月份
console.log("月份:", month);

// 獲取日期
const date = now.getDate();
console.log("日期:", date);
```

### 創建特定日期
```javascript
// 創建一個特定的日期
const birthday = new Date(2000, 5, 15); // 2000年6月15日
console.log("生日:", birthday);
```

## 解釋
在使用 Date 對象時，開發者常見的錯誤包括：
- 忘記月份是從 0 開始計算的，這可能導致日期不正確。
- 日期計算時考慮到時區差異，可能會影響到結果。
- 使用 `Date.parse()` 解析日期字符串時，格式必須正確，否則會返回 NaN。

## 一句總結
JavaScript 的 Date 對象提供了強大的功能來處理和操作日期和時間。