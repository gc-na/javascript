<!--
Meta Description: # FileSystemDirectoryHandle：JavaScript 文件系統目錄處理器 ## 簡介 `FileSystemDirectoryHandle` 是一個 JavaScript API，允許網頁應用程式以安全的方式訪問和操作用戶的本地文件系統中的目錄。此 API 主要用於提供更豐富...
Meta Keywords: await, javascript, const, filesystemdirectoryhandle, api
-->

# FileSystemDirectoryHandle：JavaScript 文件系統目錄處理器

## 簡介
`FileSystemDirectoryHandle` 是一個 JavaScript API，允許網頁應用程式以安全的方式訪問和操作用戶的本地文件系統中的目錄。此 API 主要用於提供更豐富的用戶體驗，尤其是在文件上傳和管理方面。

## 文檔
`FileSystemDirectoryHandle` 的主要目的是讓開發者能夠訪問用戶的本地文件系統中的目錄。這個接口是 File System Access API 的一部分，允許開發者讀取和寫入文件，並在用戶的確認下進行操作。

### 主要功能
- **訪問目錄**：允許開發者訪問用戶選擇的目錄。
- **列出文件**：可以列出目錄中的文件和子目錄。
- **創建和刪除文件或子目錄**：可以創建新文件或目錄，並刪除不需要的項目。

### 使用方法
使用 `FileSystemDirectoryHandle` 時，開發者需要先獲取一個 `FileSystemHandle` 實例，然後才能進行目錄操作。以下是基本的使用步驟：

1. **請求用戶選擇目錄**：
   ```javascript
   const directoryHandle = await window.showDirectoryPicker();
   ```

2. **列出目錄中的文件**：
   ```javascript
   for await (const entry of directoryHandle.values()) {
       console.log(entry.name);
   }
   ```

3. **創建新文件**：
   ```javascript
   const newFileHandle = await directoryHandle.getFileHandle('newFile.txt', { create: true });
   ```

## 範例
以下是使用 `FileSystemDirectoryHandle` 進行基本操作的範例：

### 範例 1：選擇目錄並列出文件
```javascript
async function listFiles() {
   const dirHandle = await window.showDirectoryPicker();
   for await (const entry of dirHandle.values()) {
       console.log(entry.name);
   }
}
listFiles();
```

### 範例 2：創建新文件
```javascript
async function createNewFile() {
   const dirHandle = await window.showDirectoryPicker();
   const fileHandle = await dirHandle.getFileHandle('example.txt', { create: true });
   const writable = await fileHandle.createWritable();
   await writable.write('Hello, World!');
   await writable.close();
}
createNewFile();
```

## 解釋
使用 `FileSystemDirectoryHandle` 時可能會遇到一些常見的問題：

- **權限問題**：在訪問文件系統時，必須獲得用戶的許可。如果用戶拒絕，將無法進行任何文件操作。
- **瀏覽器支持**：目前這個 API 只在某些瀏覽器中得到支持，開發者需要檢查相應的瀏覽器兼容性。
- **異步操作**：許多操作都是異步的，因此需要使用 `async/await` 或者 Promise 來處理這些操作。

## 總結
`FileSystemDirectoryHandle` 是一個強大的工具，允許 JavaScript 開發者安全地訪問和操作用戶的本地文件系統目錄。