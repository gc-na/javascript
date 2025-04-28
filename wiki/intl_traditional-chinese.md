<!--
Meta Description: # JavaScript Intl：國際化的強大工具 ## 概述 `Intl` 是一個 JavaScript 內建的物件，提供了國際化（i18n）功能，使開發者能夠在不同語言和地區之間輕鬆格式化數字、日期、時間和文字。 ## 文檔 `Intl` 物件包含多個內建的建構函式，最常用的包括 `Intl....
Meta Keywords: intl, const, new, javascript, collator
-->

# JavaScript Intl：國際化的強大工具

## 概述
`Intl` 是一個 JavaScript 內建的物件，提供了國際化（i18n）功能，使開發者能夠在不同語言和地區之間輕鬆格式化數字、日期、時間和文字。

## 文檔
`Intl` 物件包含多個內建的建構函式，最常用的包括 `Intl.NumberFormat`、`Intl.DateTimeFormat` 和 `Intl.Collator`。這些建構函式使得在不同文化背景中呈現資料變得更加簡單和一致，符合當地的格式和語言習慣。

### 目的
`Intl` 的主要目的是提供一個標準化的方法來處理國際化需求，幫助開發者創建能夠支持多語言和多地區的應用程式。

### 使用方法
使用 `Intl` 物件時，可以通過其建構函式來創建格式化物件。例如：

- `Intl.NumberFormat` 用於格式化數字。
- `Intl.DateTimeFormat` 用於格式化日期和時間。
- `Intl.Collator` 用於字串比較和排序。

### 詳細說明
- **Intl.NumberFormat**：該建構函式接受 locale 和選項參數，並返回一個數字格式化器，允許設置貨幣、百分比等格式。
  
  ```javascript
  const numberFormatter = new Intl.NumberFormat('zh-TW', {
      style: 'currency',
      currency: 'TWD'
  });
  console.log(numberFormatter.format(1000)); // NT$1,000.00
  ```

- **Intl.DateTimeFormat**：該建構函式用於格式化日期和時間，支持多種選項來定義顯示格式。
  
  ```javascript
  const dateFormatter = new Intl.DateTimeFormat('zh-TW', {
      year: 'numeric',
      month: 'long',
      day: 'numeric'
  });
  console.log(dateFormatter.format(new Date())); // 2023年10月5日
  ```

- **Intl.Collator**：該建構函式用於字串比較，支持指定語言和比較選項。
  
  ```javascript
  const collator = new Intl.Collator('zh-TW');
  const sortedArray = ['香蕉', '蘋果', '橘子'].sort(collator.compare);
  console.log(sortedArray); // ['蘋果', '橘子', '香蕉']
  ```

## 範例
以下是使用 `Intl` 的基本範例：

```javascript
// 數字格式化範例
const formatter = new Intl.NumberFormat('en-US', {
    style: 'percent'
});
console.log(formatter.format(0.25)); // 25%

// 日期格式化範例
const dateFormatter = new Intl.DateTimeFormat('fr-FR');
console.log(dateFormatter.format(new Date())); // 05/10/2023

// 字串排序範例
const fruits = ['葡萄', '香蕉', '蘋果'];
const sortedFruits = fruits.sort(new Intl.Collator('zh-TW').compare);
console.log(sortedFruits); // ['香蕉', '葡萄', '蘋果']
```

## 說明
使用 `Intl` 時，開發者需要注意以下幾點：

- **性能問題**：在大量格式化時，建議重用格式化器，避免每次都重新創建，這樣可以提高性能。
- **地區支持**：不同的瀏覽器可能對某些地區的支持程度不同，開發者應該測試所需的 locales 是否被支持。
- **選項的靈活性**：`Intl` 的選項設置非常靈活，開發者應根據需求仔細選擇，以獲得最佳的格式化效果。

## 一句總結
`Intl` 是 JavaScript 中強大的國際化工具，提供了便捷的數字、日期和字串格式化功能，幫助開發者創建多語言支持的應用程式。