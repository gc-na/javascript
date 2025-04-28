<!--
Meta Description: # JavaScript 中的 Intl：國際化 API 的完整指南 ## 概要 `Intl` 是一個 JavaScript 的內建對象，提供國際化的功能，讓開發者可以輕鬆地在應用程序中處理不同語言和地區的格式化需求。 ## 文件說明 `Intl` 對象的目的是為了支持不同文化的格式化需求，包括數字...
Meta Keywords: intl, javascript, collator, const, new
-->

# JavaScript 中的 Intl：國際化 API 的完整指南

## 概要
`Intl` 是一個 JavaScript 的內建對象，提供國際化的功能，讓開發者可以輕鬆地在應用程序中處理不同語言和地區的格式化需求。

## 文件說明
`Intl` 對象的目的是為了支持不同文化的格式化需求，包括數字、日期、時間和字符串的本地化。它提供了一系列的構造函數，例如 `Intl.NumberFormat`、`Intl.DateTimeFormat` 和 `Intl.Collator`，用以格式化數字、日期和比較字符串。

### 使用方法
要使用 `Intl`，您只需調用相應的構造函數，並傳入所需的參數。例如，要格式化一個數字，您可以這樣做：

```javascript
const numberFormatter = new Intl.NumberFormat('zh-HK', {
  style: 'currency',
  currency: 'HKD',
});
console.log(numberFormatter.format(123456.789)); // 輸出: $123,456.79
```

### 詳細說明
- **`Intl.NumberFormat`**: 用於格式化數字，支持多種選項，如貨幣、百分比等。
- **`Intl.DateTimeFormat`**: 用於格式化日期和時間，支持不同的年、月、日格式。
- **`Intl.Collator`**: 用於字符串比較，支持自定義排序規則。

## 範例
### 數字格式化
```javascript
const formatter = new Intl.NumberFormat('zh-HK', {
  style: 'decimal',
});
console.log(formatter.format(1234567.89)); // 輸出: 1,234,567.89
```

### 日期格式化
```javascript
const dateFormatter = new Intl.DateTimeFormat('zh-HK', {
  year: 'numeric',
  month: 'long',
  day: 'numeric',
});
console.log(dateFormatter.format(new Date())); // 輸出: 2023年10月30日
```

### 字符串比較
```javascript
const collator = new Intl.Collator('zh-HK');
const arr = ['香蕉', '蘋果', '橙'];
arr.sort(collator.compare);
console.log(arr); // 輸出: ['橙', '蘋果', '香蕉']
```

## 解釋
在使用 `Intl` 時，開發者應注意以下幾點：
- 確保選擇正確的語言代碼，否則可能會導致意外的格式化結果。
- 注意不同地區可能有不同的格式化規則，需根據用戶的地理位置進行調整。
- 某些舊版瀏覽器可能不支持 `Intl`，建議檢查兼容性。

## 一句總結
`Intl` 是一個強大的工具，幫助 JavaScript 開發者實現應用程序的國際化需求，支持數字、日期和字符串的本地化格式化。