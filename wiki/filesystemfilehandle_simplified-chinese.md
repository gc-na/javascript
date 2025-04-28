<!--
Meta Description: # FileSystemFileHandle 在 JavaScript 中的应用 ## 摘要 `FileSystemFileHandle` 是 Web API 中的一部分，允许开发者以编程方式访问和操作用户的文件系统，提供了一种安全的方式来读取和写入文件。 ## 文档 ### 目的 `FileSys...
Meta Keywords: await, filesystemfilehandle, const, filehandle, file
-->

# FileSystemFileHandle 在 JavaScript 中的应用

## 摘要
`FileSystemFileHandle` 是 Web API 中的一部分，允许开发者以编程方式访问和操作用户的文件系统，提供了一种安全的方式来读取和写入文件。

## 文档
### 目的
`FileSystemFileHandle` 使开发者能够处理文件的读取和写入操作，支持文件的元数据访问。它是基于用户的文件选择操作，从而保证了安全性和隐私。

### 用法
`FileSystemFileHandle` 通常与 `showOpenFilePicker` 和 `showSaveFilePicker` 配合使用，允许用户选择文件，并返回一个文件句柄。

**基本用法示例：**
```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}
```

### 详细说明
1. **获取文件句柄**：使用 `window.showOpenFilePicker()` 方法，用户可以选择一个或多个文件。
2. **读取文件内容**：通过文件句柄的 `getFile()` 方法可以获取 `File` 对象，然后可以调用 `text()`、`arrayBuffer()` 或 `blob()` 等方法读取文件内容。
3. **写入文件**：使用 `createWritable()` 方法可以获得一个可写的流，允许开发者将数据写入到用户选择的文件中。

## 示例
以下是一个简单的示例，展示了如何使用 `FileSystemFileHandle` 来读取和写入文件：

### 读取文件示例
```javascript
async function readFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log("文件内容:", contents);
}
```

### 写入文件示例
```javascript
async function writeFile() {
    const fileHandle = await window.showSaveFilePicker();
    const writable = await fileHandle.createWritable();
    await writable.write("这是写入的内容");
    await writable.close();
}
```

## 说明
- **安全性**：`FileSystemFileHandle` 需要用户主动选择文件，确保文件访问的安全性。
- **浏览器支持**：并非所有浏览器都支持 `FileSystemFileHandle`，需要检查 [Can I use](https://caniuse.com/#feat=file-system) 以确认兼容性。
- **权限管理**：用户可以随时取消文件选择或写入操作，确保了用户的控制权。

## 一句话总结
`FileSystemFileHandle` 是 JavaScript 中用于安全访问和操作用户文件的强大工具。