<!--
Meta Description: # FileList：JavaScript 中的檔案列表物件 ## 簡介 `FileList` 是一個 JavaScript 物件，用於表示一組檔案，通常是透過 `<input>` 元素的檔案上傳功能獲取的。這個物件在處理使用者上傳的多個檔案時非常有用。 ## 文檔 `FileList` 物件是由 ...
Meta Keywords: filelist, fileinput, javascript, input, file
-->

# FileList：JavaScript 中的檔案列表物件

## 簡介
`FileList` 是一個 JavaScript 物件，用於表示一組檔案，通常是透過 `<input>` 元素的檔案上傳功能獲取的。這個物件在處理使用者上傳的多個檔案時非常有用。

## 文檔
`FileList` 物件是由 `File` 物件組成的集合，`File` 物件代表使用者在檔案選擇器中選擇的單一檔案。當使用者選擇多個檔案時，這個物件會包含所有選定的檔案。`FileList` 物件常見於網頁應用程式中的檔案上傳功能。

### 目的
`FileList` 的主要目的是提供一個方式，讓開發者可以方便地存取和操作使用者上傳的檔案，無論是進行檔案驗證、顯示預覽還是將檔案送到伺服器。

### 使用方式
要使用 `FileList`，通常需要搭配 `<input type="file">` 元素。當使用者選擇檔案後，可以通過 JavaScript 獲取這個物件。例如：

```html
<input type="file" id="fileInput" multiple>
```

然後可以使用以下 JavaScript 代碼來獲取 `FileList`：

```javascript
const fileInput = document.getElementById('fileInput');
const fileList = fileInput.files; // 這裡獲取 FileList 物件
```

## 範例
以下是使用 `FileList` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>FileList 範例</title>
</head>
<body>
    <input type="file" id="fileInput" multiple>
    <button id="uploadBtn">上傳檔案</button>
    <div id="fileOutput"></div>

    <script>
        document.getElementById('uploadBtn').addEventListener('click', function() {
            const fileInput = document.getElementById('fileInput');
            const fileList = fileInput.files;
            const output = document.getElementById('fileOutput');
            output.innerHTML = '';

            for (let i = 0; i < fileList.length; i++) {
                output.innerHTML += `<p>檔案名稱: ${fileList[i].name}, 檔案大小: ${fileList[i].size} bytes</p>`;
            }
        });
    </script>
</body>
</html>
```

## 說明
在使用 `FileList` 時，開發者應注意以下幾點：

1. **多檔案上傳**：確保在 `<input>` 元素中設置 `multiple` 屬性，以允許使用者選擇多個檔案。
2. **檔案大小和類型**：開發者應進行檔案大小和類型的驗證，以避免上傳不合適的檔案。
3. **瀏覽器支援**：雖然大多數現代瀏覽器都支援 `FileList`，但某些舊版瀏覽器可能不支援此功能。

## 總結
`FileList` 是一個 JavaScript 物件，方便開發者操作使用者上傳的多個檔案。