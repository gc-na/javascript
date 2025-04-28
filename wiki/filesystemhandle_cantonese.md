<!--
Meta Description: # FileSystemHandle: JavaScript 中的文件系統處理器 ## 概要 FileSystemHandle 是一個 Web API，讓開發者能夠以更簡便的方式讀取和寫入本地文件系統中的文件和資料夾。 ## 文件說明 FileSystemHandle 主要用於提供對用戶本地文件系統...
Meta Keywords: await, filesystemhandle, const, javascript, window
-->

# FileSystemHandle: JavaScript 中的文件系統處理器

## 概要
FileSystemHandle 是一個 Web API，讓開發者能夠以更簡便的方式讀取和寫入本地文件系統中的文件和資料夾。

## 文件說明
FileSystemHandle 主要用於提供對用戶本地文件系統的訪問。這個 API 使得網頁應用程式能夠與文件進行互動而不需要使用傳統的文件上傳方法。它是 File System Access API 的一部分，提供了對文件和資料夾的安全且靈活的訪問。

### 目的
- 允許網頁應用程式直接讀取和寫入本地文件。
- 提供用戶更直觀的文件操作方式。

### 使用方式
要使用 FileSystemHandle，開發者通常需要請求用戶的許可，才能訪問特定的文件或資料夾。這通常透過 `window.showOpenFilePicker()` 或 `window.showDirectoryPicker()` 來實現。

### 詳細描述
- `FileSystemFileHandle`: 表示一個文件的句柄，提供讀取和寫入文件的功能。
- `FileSystemDirectoryHandle`: 表示一個資料夾的句柄，允許用戶列出和管理其中的文件和資料夾。

## 範例
以下是基本的使用範例：

### 讀取文件
```javascript
async function readFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}
```

### 寫入文件
```javascript
async function writeFile() {
    const newFileHandle = await window.showSaveFilePicker();
    const writable = await newFileHandle.createWritable();
    await writable.write("這是寫入的內容");
    await writable.close();
}
```

### 列出資料夾內容
```javascript
async function readDirectory() {
    const dirHandle = await window.showDirectoryPicker();
    for await (const entry of dirHandle.values()) {
        console.log(entry.name);
    }
}
```

## 解釋
- **權限**: 使用 FileSystemHandle 之前，開發者必須確保用戶已經授予必要的訪問權限。
- **安全性**: FileSystemHandle 僅能訪問用戶選擇的文件或資料夾，這樣可以保障用戶的安全和隱私。
- **瀏覽器支持**: 目前並非所有瀏覽器都支持 File System Access API，因此開發者需確保其應用在目標平台上的兼容性。

## 總結
FileSystemHandle 是一個強大的工具，允許 JavaScript 應用程式與用戶的本地文件系統進行高效、安全的互動。