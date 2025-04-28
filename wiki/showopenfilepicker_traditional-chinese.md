<!--
Meta Description: # showOpenFilePicker：JavaScript 文件選擇器 API 的詳細指南 ## 概要 `showOpenFilePicker` 是一個 JavaScript API，用於顯示文件選擇對話框，讓用戶選擇一個或多個文件。此功能可用於 Web 應用程式中，使得用戶可以輕鬆上傳文件。 ...
Meta Keywords: showopenfilepicker, javascript, api, file, promise
-->

# showOpenFilePicker：JavaScript 文件選擇器 API 的詳細指南

## 概要
`showOpenFilePicker` 是一個 JavaScript API，用於顯示文件選擇對話框，讓用戶選擇一個或多個文件。此功能可用於 Web 應用程式中，使得用戶可以輕鬆上傳文件。

## 文檔
`showOpenFilePicker` 是 File System Access API 的一部分，允許開發者訪問用戶的本地文件系統。這個方法返回一個 Promise，當用戶選擇文件後，該 Promise 將解析為一個 FileSystemFileHandle 的陣列。

### 目的
`showOpenFilePicker` 旨在提供一個簡單而直觀的方式，讓用戶選擇文件以供應用程式使用，從而提升用戶體驗。

### 用法
以下是 `showOpenFilePicker` 的基本語法：

```javascript
const fileHandles = await window.showOpenFilePicker(options);
```

### 參數
`options` 是一個可選的物件，包含配置選項，例如：

- `types`: 指定可選擇的文件類型。
- `excludeAcceptAllOption`: 如果設置為 `true`，將隱藏「接受所有」選項。
- `multiple`: 如果設置為 `true`，則允許選擇多個文件。

### 返回值
該方法返回一個 Promise，解析為一個 FileSystemFileHandle 陣列，每個 FileSystemFileHandle 都代表用戶選擇的文件。

## 範例
### 基本使用範例

```javascript
async function openFile() {
    try {
        const fileHandles = await window.showOpenFilePicker({
            types: [{
                description: 'Images',
                accept: {'image/*': ['.png', '.jpg', '.jpeg']}
            }],
            multiple: false
        });

        const file = await fileHandles[0].getFile();
        console.log('選擇的文件:', file.name);
    } catch (error) {
        console.error('錯誤:', error);
    }
}
```

## 解釋
在使用 `showOpenFilePicker` 時，開發者可能會遇到一些常見的問題：

1. **瀏覽器支持**：並非所有瀏覽器都支持 File System Access API，使用前務必檢查支持情況。
2. **安全性限制**：此方法只能在用戶的互動（例如點擊事件）中調用，否則將會拋出錯誤。
3. **文件類型過濾**：若指定的文件類型與用戶選擇的文件不匹配，則不會顯示該文件。

另外，使用 `multiple` 選項時，必須注意處理數組的返回值，確保正確處理多個文件。

## 一句總結
`showOpenFilePicker` 是一個強大的 JavaScript API，允許用戶方便地從本地文件系統中選擇文件。