<!--
Meta Description: # FileList 在 JavaScript 中的應用 ## 簡介 `FileList` 是一個 JavaScript 物件，主要用於處理用戶上傳的檔案集合。它常見於 HTML 表單中，特別是 `<input type="file">` 標籤，能讓開發者輕鬆獲取用戶選擇的檔案資訊。 ## 文檔 `...
Meta Keywords: input, files, filelist, const, javascript
-->

# FileList 在 JavaScript 中的應用

## 簡介
`FileList` 是一個 JavaScript 物件，主要用於處理用戶上傳的檔案集合。它常見於 HTML 表單中，特別是 `<input type="file">` 標籤，能讓開發者輕鬆獲取用戶選擇的檔案資訊。

## 文檔
`FileList` 物件是一個只讀的集合，包含了用戶上傳的檔案。每個檔案都以 `File` 物件的形式存在，這些物件提供了檔案的詳細資訊，例如名稱、大小和 MIME 類型。`FileList` 物件的主要用途是在網頁應用程式中接收和處理檔案上傳。

### 使用方法
當用戶選擇檔案時，可以通過 JavaScript 獲取 `FileList` 物件。以下是一個基本的示例：

```html
<input type="file" id="fileInput" multiple>
<script>
  const input = document.getElementById('fileInput');
  input.addEventListener('change', function() {
    const files = input.files; // 獲取 FileList 物件
    console.log(files);
  });
</script>
```

### 詳細說明
- **屬性與方法**：
  - `length`：返回 `FileList` 中檔案的數量。
  - `item(index)`：返回指定索引的 `File` 物件。
  
- **File 物件**：
  - `name`：檔案名稱。
  - `size`：檔案大小（以位元組為單位）。
  - `type`：檔案的 MIME 類型。

## 範例
以下是一些基本用法的示例：

### 獲取檔案名稱
```javascript
const input = document.getElementById('fileInput');
input.addEventListener('change', function() {
  const files = input.files;
  for (let i = 0; i < files.length; i++) {
    console.log(files[i].name); // 輸出檔案名稱
  }
});
```

### 獲取檔案大小
```javascript
const input = document.getElementById('fileInput');
input.addEventListener('change', function() {
  const files = input.files;
  for (let i = 0; i < files.length; i++) {
    console.log(files[i].size); // 輸出檔案大小
  }
});
```

### 使用 FileReader 讀取檔案內容
```javascript
const input = document.getElementById('fileInput');
input.addEventListener('change', function() {
  const files = input.files;
  const reader = new FileReader();
  reader.onload = function(event) {
    console.log(event.target.result); // 輸出檔案內容
  };
  reader.readAsText(files[0]); // 讀取第一個檔案
});
```

## 解釋
在使用 `FileList` 時，開發者應注意以下幾點：
- **只讀性**：`FileList` 是只讀的，無法直接修改其內容。
- **文件類型**：在處理檔案時，應確保檔案類型符合預期，以避免錯誤。
- **性能考量**：對於大型檔案，使用 `FileReader` 時要小心，避免阻塞主線程。

## 一句總結
`FileList` 是一個只讀的檔案集合，提供用戶上傳檔案的詳細資訊，讓開發者可以輕鬆管理檔案操作。