<!--
Meta Description: # showDirectoryPicker: JavaScript 中的目录选择器接口 ## 概述 `showDirectoryPicker` 是一个用于打开文件系统访问 API 的方法，允许用户选择一个目录并获取该目录的引用。该方法在 Web 应用中非常有用，特别是在需要操作用户文件时。 ## 文...
Meta Keywords: showdirectorypicker, error, javascript, directoryhandle, await
-->

# showDirectoryPicker: JavaScript 中的目录选择器接口

## 概述
`showDirectoryPicker` 是一个用于打开文件系统访问 API 的方法，允许用户选择一个目录并获取该目录的引用。该方法在 Web 应用中非常有用，特别是在需要操作用户文件时。

## 文档
### 目的
`showDirectoryPicker` 方法的主要目的是提供一种用户友好的方式，让用户可以选择一个目录，而不仅仅是单个文件。这对于需要处理多个文件或结构化数据的应用程序尤为重要。

### 用法
`showDirectoryPicker` 方法返回一个 Promise，该 Promise 解析为一个 `FileSystemDirectoryHandle` 对象，代表用户选择的目录。

#### 语法
```javascript
let directoryHandle = await showDirectoryPicker();
```

### 参数
`showDirectoryPicker` 方法不接受任何参数。

### 返回值
- 返回一个 Promise，解决为 `FileSystemDirectoryHandle` 对象。

### 可用性
- 该方法需要在安全上下文中使用（例如 HTTPS）。
- 需要浏览器支持文件系统访问 API。

## 示例
### 基本用法
下面是一个使用 `showDirectoryPicker` 方法的基本示例：

```javascript
async function getDirectory() {
    try {
        const directoryHandle = await showDirectoryPicker();
        console.log('用户选择的目录:', directoryHandle.name);
    } catch (error) {
        console.error('目录选择失败:', error);
    }
}

getDirectory();
```

### 遍历目录中的文件
您可以使用 `FileSystemDirectoryHandle` 对象来遍历目录中的文件：

```javascript
async function listFilesInDirectory() {
    try {
        const directoryHandle = await showDirectoryPicker();
        for await (const entry of directoryHandle.values()) {
            console.log('文件或目录名称:', entry.name);
        }
    } catch (error) {
        console.error('无法列出文件:', error);
    }
}

listFilesInDirectory();
```

## 解释
### 常见问题与注意事项
- **权限问题**：用户必须授权访问文件系统，因此确保处理用户拒绝授权的情况。
- **浏览器兼容性**：并非所有浏览器都支持文件系统访问 API，建议检查支持情况。
- **异步处理**：`showDirectoryPicker` 是一个异步方法，因此需要使用 `async/await` 或 `.then()` 进行处理。
- **安全上下文**：该方法只能在 HTTPS 环境中使用，确保您的应用程序遵循这一要求。

## 一句话总结
`showDirectoryPicker` 是 JavaScript 中用于让用户选择目录的有效方法，简化了文件系统交互。