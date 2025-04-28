<!--
Meta Description: # JavaScript 中的檔案處理：File 對象的全面指南 ## 簡介 在 JavaScript 中，File 對象用於表示用戶透過文件選擇器選擇的檔案。這使得開發者可以在網頁應用中輕鬆地處理用戶上傳的檔案，例如圖像、文檔等。 ## 文檔 ### 目的 File 對象是用來表示本地檔案的，通常...
Meta Keywords: file, type, javascript, filelist, input
-->

# JavaScript 中的檔案處理：File 對象的全面指南

## 簡介
在 JavaScript 中，File 對象用於表示用戶透過文件選擇器選擇的檔案。這使得開發者可以在網頁應用中輕鬆地處理用戶上傳的檔案，例如圖像、文檔等。

## 文檔
### 目的
File 對象是用來表示本地檔案的，通常和 FileList 對象一起使用，FileList 是一個檔案的集合，代表用戶透過 `<input type="file">` 元素選擇的檔案。

### 使用方法
File 對象的實例可以通過以下方式獲得：
1. 使用 `<input type="file">` 元素來讓用戶選擇檔案。
2. 在 JavaScript 中通過 `files` 屬性獲取 FileList 對象，並從中提取 File 對象。

### 詳細說明
#### File 對象的屬性
- **name**: 檔案的名稱（包括擴展名）。
- **size**: 檔案的大小（以字節為單位）。
- **type**: 檔案的 MIME 類型（如 `image/jpeg`）。
- **lastModified**: 檔案的最後修改時間（以時間戳表示）。

#### File 對象的方法
File 對象本身不包含方法，但可以使用 `FileReader` 來讀取檔案內容。

## 示例
以下是一個基本的使用示例：

```html
<input type="file" id="fileInput" />
<script>
  document.getElementById('fileInput').addEventListener('change', function(event) {
    const file = event.target.files[0]; // 獲取第一個檔案
    console.log('檔案名稱:', file.name);
    console.log('檔案大小:', file.size, '字節');
    console.log('檔案類型:', file.type);
  });
</script>
```

## 解釋
### 常見問題
- **檔案類型檢查**: 當用戶上傳檔案時，應檢查檔案的 `type` 屬性以確保檔案格式正確。
- **檔案大小限制**: 在處理上傳檔案時，應考慮 `size` 屬性來限制檔案大小，避免上傳過大的檔案。
- **跨瀏覽器兼容性**: 注意不同瀏覽器對 File API 的支持情況，確保應用在各種環境中正常運行。

## 總結
File 對象是 JavaScript 中用於表示和處理用戶上傳檔案的關鍵組件，提供了對檔案屬性的訪問和操作能力。