<!--
Meta Description: # showDirectoryPicker：JavaScript 中的目錄選擇器 API ## 概述 `showDirectoryPicker` 是一個 JavaScript API，允許用戶選擇一個目錄，並在 Web 應用中進行文件系統操作。這個功能可以幫助開發者獲取用戶的目錄路徑，從而方便地進行...
Meta Keywords: showdirectorypicker, javascript, api, async, directoryhandle
-->

# showDirectoryPicker：JavaScript 中的目錄選擇器 API

## 概述
`showDirectoryPicker` 是一個 JavaScript API，允許用戶選擇一個目錄，並在 Web 應用中進行文件系統操作。這個功能可以幫助開發者獲取用戶的目錄路徑，從而方便地進行文件管理和處理。

## 文檔
### 目的
`showDirectoryPicker` 的主要目的是提供一種簡便的方式，讓用戶能夠選擇他們的文件系統中的一個目錄，並且允許應用程序訪問該目錄內的文件。

### 用法
要使用 `showDirectoryPicker`，需在支持的瀏覽器中調用該方法。這是一個 async 函數，因此通常需要在 `async` 上下文中使用。

```javascript
async function selectDirectory() {
    const directoryHandle = await window.showDirectoryPicker();
    console.log(directoryHandle);
}
```

### 詳細說明
- **返回值**：此方法返回一個 `FileSystemDirectoryHandle` 對象，代表所選的目錄。
- **權限**：用戶必須明確授權應用程序訪問所選目錄，這意味著安全性得到保證。
- **錯誤處理**：在調用此方法時，建議使用 `try...catch` 結構來捕獲可能的錯誤，例如用戶取消選擇或瀏覽器不支持該 API。

## 範例
以下是一個簡單的示例，展示如何使用 `showDirectoryPicker` 獲取目錄：

```javascript
async function getDirectoryFiles() {
    try {
        const directoryHandle = await window.showDirectoryPicker();
        for await (const entry of directoryHandle.values()) {
            console.log(entry.name); // 輸出目錄內的所有文件和子目錄名稱
        }
    } catch (error) {
        console.error('錯誤:', error);
    }
}
```

## 解釋
- **常見陷阱**：
  - 確保在支持的瀏覽器中使用該功能，如 Chrome 和 Edge。
  - 了解用戶的選擇是暫時的，只有在用戶再次授權後，才能再次訪問選定的目錄。

- **注意事項**：
  - 使用 `showDirectoryPicker` 時，應考慮用戶的隱私和數據安全，避免不必要的數據存取。
  - 此 API 仍在積極開發中，可能會在未來的版本中進行更新或改變。

## 簡短總結
`showDirectoryPicker` 是一個強大的 JavaScript API，允許用戶選擇目錄以便進行文件系統操作，增強了 Web 應用的交互性和功能性。