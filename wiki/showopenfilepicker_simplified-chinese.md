<!--
Meta Description: # showOpenFilePicker：JavaScript 文件选择器 API ## 概述 `showOpenFilePicker` 是一个用于在 Web 应用程序中打开文件选择对话框的 JavaScript API。它允许用户选择一个或多个文件，并返回一个文件句柄，用于后续的文件操作。 ## ...
Meta Keywords: showopenfilepicker, file, const, javascript, await
-->

# showOpenFilePicker：JavaScript 文件选择器 API

## 概述
`showOpenFilePicker` 是一个用于在 Web 应用程序中打开文件选择对话框的 JavaScript API。它允许用户选择一个或多个文件，并返回一个文件句柄，用于后续的文件操作。

## 文档
`showOpenFilePicker` 方法是 File System Access API 的一部分，旨在提供更直接的文件系统访问。这个方法可以让开发者创建一个自定义的文件选择器，用户在选择文件后，可以进行进一步的处理。

### 用法
```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    console.log(file.name);
}
```

### 参数
`showOpenFilePicker` 方法没有参数，但它可以接收一个配置对象，允许开发者指定文件类型、是否允许多选等选项。

### 返回值
该方法返回一个 Promise，解析为一个包含所选文件句柄的数组。如果用户取消操作，则返回一个拒绝的 Promise。

### 配置选项
开发者可以传递以下选项：
- `types`: 允许的文件类型数组
- `excludeAcceptAllOption`: 是否排除接受所有选项
- `multiple`: 是否允许选择多个文件

## 示例
### 基本用法
```javascript
async function selectFiles() {
    try {
        const fileHandles = await window.showOpenFilePicker({
            types: [{
                description: '图片文件',
                accept: {'image/*': ['.png', '.jpg', '.jpeg']}
            }],
            multiple: true
        });
        
        for (const handle of fileHandles) {
            const file = await handle.getFile();
            console.log(file.name);
        }
    } catch (err) {
        console.error(err);
    }
}
```

### 处理用户取消选择
```javascript
async function openFile() {
    try {
        const [fileHandle] = await window.showOpenFilePicker();
        const file = await fileHandle.getFile();
        console.log(file.name);
    } catch (err) {
        if (err.name === 'AbortError') {
            console.log('用户已取消选择。');
        } else {
            console.error(err);
        }
    }
}
```

## 说明
在使用 `showOpenFilePicker` 时，有一些常见的注意事项：
- **浏览器兼容性**: 该 API 目前在一些现代浏览器中支持，包括 Chrome 和 Edge，但不支持 Firefox 和 Safari。
- **HTTPS**: 该功能仅在安全上下文（如 HTTPS）中可用。
- **权限问题**: 用户需要允许访问文件系统，且每次选择文件时都需要进行确认。

## 一句话总结
`showOpenFilePicker` 是一个现代的 JavaScript 方法，用于访问用户文件系统并选择文件。