<!--
Meta Description: # FileSystemDirectoryHandle：JavaScript 中的文件系統目錄句柄 ## 概述 `FileSystemDirectoryHandle` 是一個 JavaScript 的 Web API，允許開發者以安全的方式訪問和操作用戶的文件系統目錄。透過這個 API，開發者可以在...
Meta Keywords: filesystemdirectoryhandle, await, const, javascript, dirhandle
-->

# FileSystemDirectoryHandle：JavaScript 中的文件系統目錄句柄

## 概述
`FileSystemDirectoryHandle` 是一個 JavaScript 的 Web API，允許開發者以安全的方式訪問和操作用戶的文件系統目錄。透過這個 API，開發者可以在用戶的授權下讀取、寫入和管理文件和子目錄。

## 文檔
`FileSystemDirectoryHandle` 是 File System Access API 的一部分，旨在提供一個簡化的界面，讓 Web 應用能夠直接與用戶的文件系統進行交互。開發者可以使用此 API 來打開、創建和管理文件夾及其內容。

### 目的
`FileSystemDirectoryHandle` 可以幫助開發者實現以下功能：
- 瀏覽用戶的文件系統。
- 創建新的文件或文件夾。
- 讀取和修改現有文件。

### 使用
在使用 `FileSystemDirectoryHandle` 之前，開發者需要獲得用戶的授權。這可以通過 `showDirectoryPicker()` 方法來實現，該方法會顯示一個文件選擇器對話框，讓用戶選擇一個目錄。

#### 獲取目錄句柄的基本步驟：
1. 使用 `window.showDirectoryPicker()` 獲取 `FileSystemDirectoryHandle`。
2. 使用該句柄進行文件和目錄的操作。

### 方法
- `getFileHandle(name: string, options?: FileHandleOptions): Promise<FileSystemFileHandle>` - 獲取指定名稱的文件句柄。
- `getDirectoryHandle(name: string, options?: DirectoryHandleOptions): Promise<FileSystemDirectoryHandle>` - 獲取指定名稱的子目錄句柄。
- `removeEntry(name: string, options?: { recursive: boolean }): Promise<void>` - 刪除指定的文件或子目錄。

## 範例
以下是一些使用 `FileSystemDirectoryHandle` 的基本範例：

### 獲取目錄句柄
```javascript
async function getDirectory() {
    const dirHandle = await window.showDirectoryPicker();
    console.log(dirHandle);
}
getDirectory();
```

### 創建文件
```javascript
async function createFile() {
    const dirHandle = await window.showDirectoryPicker();
    const fileHandle = await dirHandle.getFileHandle('example.txt', { create: true });
    const writable = await fileHandle.createWritable();
    await writable.write('Hello, World!');
    await writable.close();
}
createFile();
```

### 讀取文件
```javascript
async function readFile() {
    const dirHandle = await window.showDirectoryPicker();
    const fileHandle = await dirHandle.getFileHandle('example.txt');
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}
readFile();
```

## 解釋
使用 `FileSystemDirectoryHandle` 時需要注意以下幾點：
- 確保用戶已授權訪問文件系統。
- 操作文件時，務必處理異常情況，如文件不存在或無法讀取。
- 支持的瀏覽器可能有限，建議檢查兼容性。

## 一句總結
`FileSystemDirectoryHandle` 使 JavaScript 開發者能夠以安全的方式直接訪問和管理用戶的文件系統目錄。