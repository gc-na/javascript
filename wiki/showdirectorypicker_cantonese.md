<!--
Meta Description: # showDirectoryPicker：JavaScript 中的目錄選擇器功能 ## 簡介 `showDirectoryPicker` 是一個 JavaScript API，允許用戶選擇一個目錄，並通過 Web 應用程序訪問該目錄中的文件。這個功能特別適合需要用戶上傳多個文件或管理文件結構的應...
Meta Keywords: showdirectorypicker, javascript, directoryhandle, error, await
-->

# showDirectoryPicker：JavaScript 中的目錄選擇器功能

## 簡介
`showDirectoryPicker` 是一個 JavaScript API，允許用戶選擇一個目錄，並通過 Web 應用程序訪問該目錄中的文件。這個功能特別適合需要用戶上傳多個文件或管理文件結構的應用。

## 文檔

### 目的
`showDirectoryPicker` 的主要目的在於提供一種簡單的方式，讓用戶能夠選擇一個目錄，然後可以在 JavaScript 中進行操作。這對於需要處理大量文件的應用程序非常有用。

### 使用
要使用 `showDirectoryPicker`，你需要在一個異步函數中調用它，因為它返回一個 Promise。以下是基本的語法：

```javascript
async function selectDirectory() {
    const directoryHandle = await window.showDirectoryPicker();
    // 進一步處理 directoryHandle
}
```

### 詳細說明
- **返回值**：`showDirectoryPicker` 返回一個 `FileSystemDirectoryHandle` 對象，這個對象代表用戶所選擇的目錄。
- **權限**：用戶在選擇目錄後，應用程序可以訪問該目錄下的文件，但必須遵循用戶的權限設定。
- **錯誤處理**：由於此操作是異步的，建議使用 try-catch 塊來捕獲可能的錯誤。

## 範例

### 基本用法
以下是一個簡單的例子，展示如何使用 `showDirectoryPicker`：

```javascript
async function selectDirectory() {
    try {
        const directoryHandle = await window.showDirectoryPicker();
        console.log('選擇的目錄:', directoryHandle.name);
    } catch (error) {
        console.error('選擇目錄時發生錯誤:', error);
    }
}

selectDirectory();
```

### 列出目錄中的文件
下面的範例展示如何列出所選目錄中的文件：

```javascript
async function listFilesInDirectory() {
    try {
        const directoryHandle = await window.showDirectoryPicker();
        for await (const entry of directoryHandle.values()) {
            console.log('文件名:', entry.name);
        }
    } catch (error) {
        console.error('列出文件時發生錯誤:', error);
    }
}

listFilesInDirectory();
```

## 解釋
- **常見問題**：在某些瀏覽器中，此功能可能尚未完全支持，因此建議檢查瀏覽器的兼容性。
- **權限問題**：用戶必須授予訪問權限，否則將無法成功選擇目錄。
- **異步操作**：由於 `showDirectoryPicker` 是異步的，確保在調用該函數時使用 `await`。

## 總結
`showDirectoryPicker` 是一個強大的 API，允許用戶在 JavaScript 應用中選擇目錄，並能有效地管理文件。