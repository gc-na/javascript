<!--
Meta Description: # FileSystemFileHandle 於 JavaScript 的應用 ## 簡介 FileSystemFileHandle 係一個以 JavaScript 操作檔案系統嘅新 API，容許開發者直接訪問用戶檔案，並提供讀取及寫入檔案嘅功能。 ## 文件 ### 目的 FileSystemFi...
Meta Keywords: filesystemfilehandle, await, const, javascript, filehandle
-->

# FileSystemFileHandle 於 JavaScript 的應用

## 簡介
FileSystemFileHandle 係一個以 JavaScript 操作檔案系統嘅新 API，容許開發者直接訪問用戶檔案，並提供讀取及寫入檔案嘅功能。

## 文件
### 目的
FileSystemFileHandle 主要用於改善網頁應用程序嘅檔案處理能力，令開發者可以更方便地讀取、寫入及管理用戶檔案。

### 使用方法
FileSystemFileHandle 通常與 File System Access API 共同使用。開發者可以通過 `window.showOpenFilePicker()` 來選擇檔案，然後取得 FileSystemFileHandle 來進行檔案操作。

### 詳細說明
- **創建文件句柄**: 使用 `showOpenFilePicker()` 或 `showSaveFilePicker()` 方法可創建文件句柄。
- **讀取檔案**: 通過 `getFile()` 方法可以獲取檔案對象，然後使用 `FileReader` 或 `Response` 來讀取檔案內容。
- **寫入檔案**: 使用 `createWritable()` 方法可獲得可寫入的流，並可以使用 `write()` 方法將數據寫入檔案。

## 範例
### 基本用法
```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}

async function saveFile() {
    const fileHandle = await window.showSaveFilePicker();
    const writable = await fileHandle.createWritable();
    await writable.write('Hello World!');
    await writable.close();
}
```

## 說明
- **權限問題**: 使用 FileSystemFileHandle 時，必須獲得用戶同意才能訪問檔案，這可能會引起權限錯誤。
- **兼容性**: 目前並非所有瀏覽器都支持這個 API，因此在使用前需檢查瀏覽器的兼容性。
- **錯誤處理**: 開發者需要注意異常情況，例如用戶取消選擇檔案或者檔案無法訪問等情況。

## 單句總結
FileSystemFileHandle 提供了強大的檔案操作功能，讓 JavaScript 開發者能夠更靈活地處理用戶檔案。