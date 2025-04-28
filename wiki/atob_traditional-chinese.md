<!--
Meta Description: # JavaScript 中的 atob 函數：解碼 Base64 字符串 ## 簡介 `atob` 是 JavaScript 的一個內建函數，用於將 Base64 編碼的字符串解碼為普通字符串。Base64 編碼常用於在網絡上安全傳輸二進制數據。 ## 文檔 ### 目的 `atob` 函數的主要...
Meta Keywords: atob, base64, javascript, const, console
-->

# JavaScript 中的 atob 函數：解碼 Base64 字符串

## 簡介
`atob` 是 JavaScript 的一個內建函數，用於將 Base64 編碼的字符串解碼為普通字符串。Base64 編碼常用於在網絡上安全傳輸二進制數據。

## 文檔
### 目的
`atob` 函數的主要目的是將 Base64 編碼的數據轉換回原始的二進制字符串。這在處理 Web API 返回的數據或從數據 URI 中提取信息時非常有用。

### 使用方式
`atob` 函數的語法如下：
```javascript
atob(encodedString);
```
- `encodedString`：要解碼的 Base64 編碼字符串。

### 返回值
該函數返回一個解碼後的字符串，該字符串是原始數據的文本表示。

## 示例
### 基本用法
```javascript
// Base64 編碼的字符串
const base64String = 'SGVsbG8sIFdvcmxkIQ==';

// 使用 atob 解碼
const decodedString = atob(base64String);

// 輸出解碼結果
console.log(decodedString); // "Hello, World!"
```

### 實際應用
在處理從服務器獲取的 Base64 編碼數據時，可以這樣使用：
```javascript
const imageData = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUA...';
const base64Part = imageData.split(',')[1]; // 獲取 Base64 部分
const decodedImage = atob(base64Part); // 解碼

console.log(decodedImage); // 輸出解碼後的圖像數據
```

## 說明
- **字符集限制**：`atob` 函數只支持 ASCII 字符，對於包含多字節字符（如 UTF-8）的字符串，需先進行編碼轉換。
- **異常處理**：如果傳入的字符串不是有效的 Base64 編碼，`atob` 會拋出錯誤。建議在使用時加上錯誤處理：
    ```javascript
    try {
        const decoded = atob(invalidBase64String);
    } catch (e) {
        console.error('解碼失敗:', e);
    }
    ```
- **安全性**：由於 `atob` 解碼任何 Base64 字符串，應避免處理未經信任的數據，以防止安全漏洞。

## 一句總結
`atob` 是一個 JavaScript 函數，用於將 Base64 編碼的字符串解碼為普通字符串。