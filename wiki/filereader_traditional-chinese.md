<!--
Meta Description: # JavaScript 的 FileReader API 詳細介紹 ## 概述 FileReader 是一個 JavaScript API，允許網頁應用程式異步讀取用戶選擇的檔案內容，這些檔案通常是從 `<input type="file">` 元素上傳的。通過 FileReader，開發者可以輕...
Meta Keywords: filereader, file, fileinput, const, reader
-->

# JavaScript 的 FileReader API 詳細介紹

## 概述
FileReader 是一個 JavaScript API，允許網頁應用程式異步讀取用戶選擇的檔案內容，這些檔案通常是從 `<input type="file">` 元素上傳的。通過 FileReader，開發者可以輕鬆地處理檔案，以便進行顯示或進一步操作。

## 文檔
FileReader 物件提供了多種方法來讀取檔案，包括：

- **readAsText(file)**: 以純文字格式讀取檔案。
- **readAsDataURL(file)**: 將檔案讀取為 Data URL，通常用於顯示圖像。
- **readAsArrayBuffer(file)**: 讀取檔案為 ArrayBuffer，適合處理二進制資料。
- **readAsBinaryString(file)**: 讀取檔案為二進制字符串（不推薦使用，因為在最新標準中已被棄用）。

### 使用方法
要使用 FileReader，首先需創建一個 FileReader 實例，然後可以調用其方法來讀取檔案，最後通過事件處理程序來處理讀取完成後的結果。

```javascript
const fileInput = document.getElementById('fileInput');
const reader = new FileReader();

reader.onload = function(event) {
    console.log(event.target.result); // 讀取的檔案內容
};

fileInput.addEventListener('change', function() {
    const file = fileInput.files[0]; // 獲取選擇的檔案
    if (file) {
        reader.readAsText(file); // 開始讀取檔案
    }
});
```

## 範例
以下是 FileReader 的一些基本使用範例：

### 1. 讀取文本檔案
```javascript
const fileInput = document.getElementById('fileInput');
const reader = new FileReader();

reader.onload = function(event) {
    console.log('檔案內容:', event.target.result);
};

fileInput.addEventListener('change', function() {
    const file = fileInput.files[0];
    if (file) {
        reader.readAsText(file);
    }
});
```

### 2. 讀取圖像並顯示
```javascript
const fileInput = document.getElementById('fileInput');
const reader = new FileReader();
const img = document.getElementById('imageDisplay');

reader.onload = function(event) {
    img.src = event.target.result; // 為圖像元素設定來源
};

fileInput.addEventListener('change', function() {
    const file = fileInput.files[0];
    if (file) {
        reader.readAsDataURL(file);
    }
});
```

## 解釋
在使用 FileReader 時，開發者應注意以下幾點：

- **異步操作**: FileReader 的讀取方法是異步的，這意味著在讀取完成之前，程式不會等待，因此需要設置事件處理程序來獲取結果。
- **檔案大小限制**: 瀏覽器可能對上傳的檔案大小有限制，開發者應考慮用戶的體驗，並提供足夠的錯誤處理。
- **安全性考量**: FileReader 僅能讀取用戶選擇的檔案，無法隨意訪問檔案系統，這有助於保護用戶的隱私。

## 簡短總結
FileReader 是一個強大的 JavaScript API，用於異步讀取用戶選擇的檔案，提供多種格式的讀取選項。