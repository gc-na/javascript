<!--
Meta Description: # showOpenFilePicker：JavaScript 中的檔案選擇器 API ## 概要 `showOpenFilePicker` 是一個 JavaScript API，允許用戶輕鬆打開本地檔案選擇對話框，並選擇一個或多個檔案。這個功能通常用於需要用戶上傳或選擇檔案的 Web 應用程式中。...
Meta Keywords: showopenfilepicker, file, const, await, javascript
-->

# showOpenFilePicker：JavaScript 中的檔案選擇器 API

## 概要
`showOpenFilePicker` 是一個 JavaScript API，允許用戶輕鬆打開本地檔案選擇對話框，並選擇一個或多個檔案。這個功能通常用於需要用戶上傳或選擇檔案的 Web 應用程式中。

## 文檔
`showOpenFilePicker` 方法是 File System Access API 的一部分，旨在提供更直觀的檔案存取方式。這個方法允許開發者直接從用戶的檔案系統中選擇檔案，而無需使用傳統的 `<input type="file">` 元素。

### 目的
`showOpenFilePicker` 的主要目的是讓開發者能夠提供更好的用戶體驗，使得用戶能夠直接選擇所需的檔案，而不必經過多個步驟。

### 使用方法
```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    console.log(file.name);
}
```

### 參數
- 此方法不接受任何參數，返回一個 Promise，該 Promise 解決為一個檔案句柄數組。

### 返回值
- 返回一個包含用戶選擇檔案的 `FileSystemFileHandle` 物件的陣列。

## 示例
### 基本用法
```javascript
async function pickFile() {
    try {
        const [fileHandle] = await window.showOpenFilePicker();
        const file = await fileHandle.getFile();
        console.log(`選擇的檔案: ${file.name}`);
    } catch (err) {
        console.error('選擇檔案時出現錯誤:', err);
    }
}
```

### 多檔案選擇
```javascript
async function pickMultipleFiles() {
    const options = {
        multiple: true
    };
    try {
        const fileHandles = await window.showOpenFilePicker(options);
        for (const fileHandle of fileHandles) {
            const file = await fileHandle.getFile();
            console.log(`選擇的檔案: ${file.name}`);
        }
    } catch (err) {
        console.error('選擇檔案時出現錯誤:', err);
    }
}
```

## 解釋
### 常見陷阱
1. **瀏覽器支持**：`showOpenFilePicker` 目前僅在部分現代瀏覽器中受支持，如 Chrome 和 Edge。使用前需確認用戶的瀏覽器兼容性。
2. **使用者授權**：在某些情況下，使用者可能需要授權網站訪問其檔案系統。如果用戶拒絕，則會拋出錯誤。
3. **CORS 問題**：選擇的檔案如果涉及跨域存取，可能需要處理 CORS 設定。

### 附加說明
- `showOpenFilePicker` 方法是異步的，因此應使用 `async/await` 或 `.then()` 進行處理。
- 返回的檔案句柄可以用於後續的檔案操作，如讀取檔案內容或刪除檔案。

## 一句總結
`showOpenFilePicker` 是一個強大的 JavaScript API，能夠簡化檔案選擇過程，提升用戶的操作體驗。