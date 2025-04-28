<!--
Meta Description: # FormData：JavaScript 中的表單數據處理工具 ## 概述 `FormData` 是一個 JavaScript 內建的接口，用於構造一組鍵值對，這些鍵值對代表表單數據，並可以輕鬆地用於傳送到伺服器。 ## 文件 ### 目的 `FormData` 的主要目的是方便地收集和處理用戶提...
Meta Keywords: formdata, javascript, const, formelement, error
-->

# FormData：JavaScript 中的表單數據處理工具

## 概述
`FormData` 是一個 JavaScript 內建的接口，用於構造一組鍵值對，這些鍵值對代表表單數據，並可以輕鬆地用於傳送到伺服器。

## 文件
### 目的
`FormData` 的主要目的是方便地收集和處理用戶提交的表單數據，尤其是在使用 AJAX 請求時。

### 用法
要使用 `FormData`，首先需要創建一個新的 `FormData` 物件，通常是從一個表單元素中創建。這樣可以自動提取該表單的所有輸入數據。

```javascript
const formElement = document.querySelector('form');
const formData = new FormData(formElement);
```

### 詳細說明
- `FormData` 物件可以直接將 form 元素作為參數傳遞，也可以使用 `append()` 方法手動添加數據。
- 這個接口支持多種數據類型，包括文本、文件等。
- 你可以使用 `forEach` 方法遍歷所有表單數據。

## 示例
### 基本用法
```javascript
// 假設有一個表單
const formElement = document.querySelector('form');
const formData = new FormData(formElement);

// 使用 forEach 遍歷表單數據
formData.forEach((value, key) => {
    console.log(key, value);
});

// 添加額外數據
formData.append('extraField', 'extraValue');
```

### 透過 Fetch API 發送數據
```javascript
fetch('/submit', {
    method: 'POST',
    body: formData
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

## 解釋
- **常見問題**：在使用 `FormData` 時，可能會忘記設置正確的 Content-Type 標頭。當使用 `FormData` 時，瀏覽器會自動設置適當的 Content-Type，無需手動設置。
- **獲取數據**：注意，使用 `FormData` 獲取數據時，不能直接使用 `formData` 物件來檢查是否有某個特定的鍵。你需要使用 `has()` 方法來確認鍵的存在。
- **文件上傳**：`FormData` 特別適合用於文件上傳，因為它支持 Blob 對象。

## 總結
`FormData` 在 JavaScript 中是一個強大的工具，用於輕鬆處理和傳送表單數據。