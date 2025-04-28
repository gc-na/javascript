<!--
Meta Description: # showSaveFilePicker：JavaScript 中的文件保存對話框選擇器 ## Synopsis `showSaveFilePicker` 是一個瀏覽器 API，用於顯示文件保存對話框，讓用戶選擇文件的保存路徑及文件名，並返回所選文件的 FileSystemFileHandle。 #...
Meta Keywords: error, showsavefilepicker, options, javascript, const
-->

# showSaveFilePicker：JavaScript 中的文件保存對話框選擇器

## Synopsis
`showSaveFilePicker` 是一個瀏覽器 API，用於顯示文件保存對話框，讓用戶選擇文件的保存路徑及文件名，並返回所選文件的 FileSystemFileHandle。

## Documentation
`showSaveFilePicker` 是 Web API 的一部分，專為提供用戶友好的文件保存體驗而設計。這個方法允許開發者在 Web 應用中直接調用系統的文件保存對話框，使用戶可以選擇保存文件的位置和名稱。

### Purpose
- 提高用戶的文件保存體驗。
- 允許用戶在本地文件系統中選擇保存文件的路徑。

### Usage
這個方法是異步的，因此它會返回一個 Promise。使用時，開發者可以通過以下方式調用：

```javascript
const options = {
  suggestedName: 'default.txt',
  types: [
    {
      description: 'Text Files',
      accept: {'text/plain': ['.txt']},
    },
  ],
};

showSaveFilePicker(options).then(fileHandle => {
  // 處理返回的文件句柄
}).catch(error => {
  console.error('Error selecting file:', error);
});
```

### Parameters
- `options` (可選)：一個包含建議文件名及文件類型的選項對象。
  - `suggestedName` (string)：建議的文件名。
  - `types` (array)：文件類型的描述，允許用戶選擇特定的文件格式。

## Examples
1. **基本用法：**
   ```javascript
   async function saveFile() {
     const options = {
       suggestedName: 'myFile.txt',
       types: [
         {
           description: 'Text Files',
           accept: {'text/plain': ['.txt']},
         },
       ],
     };

     try {
       const fileHandle = await showSaveFilePicker(options);
       console.log('Selected file handle:', fileHandle);
     } catch (error) {
       console.error('Failed to show save file picker:', error);
     }
   }

   saveFile();
   ```

2. **帶有不同文件類型的選擇：**
   ```javascript
   async function saveImageFile() {
     const options = {
       suggestedName: 'image.png',
       types: [
         {
           description: 'PNG Images',
           accept: {'image/png': ['.png']},
         },
         {
           description: 'JPEG Images',
           accept: {'image/jpeg': ['.jpg', '.jpeg']},
         },
       ],
     };

     try {
       const fileHandle = await showSaveFilePicker(options);
       console.log('Image file handle selected:', fileHandle);
     } catch (error) {
       console.error('Error in saving image:', error);
     }
   }

   saveImageFile();
   ```

## Explanation
在使用 `showSaveFilePicker` 時，開發者需注意以下幾點：
- 確保瀏覽器支持該 API，因為不是所有瀏覽器都支持。
- 使用此方法時，必須在用戶的交互事件（如點擊按鈕）中調用，否則可能會導致錯誤。
- 回傳的文件句柄需要進一步處理，例如寫入數據。

## One Line Summary
`showSaveFilePicker` 是一個用於顯示文件保存對話框的 JavaScript API，讓用戶方便地選擇文件的保存位置和名稱。