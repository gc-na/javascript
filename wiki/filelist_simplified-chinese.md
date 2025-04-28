<!--
Meta Description: # JavaScript中的FileList：文件列表对象详解 ## 概述 FileList是JavaScript中的一个内置对象，主要用于处理用户通过文件输入控件选择的文件列表。它提供了一种简单的方式来访问和操作多个文件的信息，广泛应用于文件上传和处理场景。 ## 文档 ### 目的 FileLi...
Meta Keywords: input, file, filelist, const, document
-->

# JavaScript中的FileList：文件列表对象详解

## 概述
FileList是JavaScript中的一个内置对象，主要用于处理用户通过文件输入控件选择的文件列表。它提供了一种简单的方式来访问和操作多个文件的信息，广泛应用于文件上传和处理场景。

## 文档
### 目的
FileList对象用于表示用户选择的文件集合，通常与HTML中的`<input type="file">`元素结合使用。每当用户选择文件时，FileList对象会更新，以反映当前选择的文件。

### 用法
FileList对象是一个只读集合，包含多个File对象。File对象表示单个文件的属性，例如文件名、文件大小和文件类型等。可以通过`input`元素的`files`属性访问FileList。

### 相关属性
- `length`: 返回FileList中包含的文件数量。
- `item(index)`: 返回指定索引位置的File对象。

## 示例
### 基本用法
以下是一个简单的示例，展示如何使用FileList对象获取用户选择的文件信息：
```html
<input type="file" id="fileInput" multiple>
<button id="uploadBtn">上传文件</button>
<div id="fileList"></div>

<script>
document.getElementById('uploadBtn').addEventListener('click', function() {
    const input = document.getElementById('fileInput');
    const fileList = input.files;
    const output = document.getElementById('fileList');
    
    output.innerHTML = ''; // 清空之前的内容

    for (let i = 0; i < fileList.length; i++) {
        const file = fileList.item(i);
        output.innerHTML += `<p>文件名: ${file.name}, 文件大小: ${file.size} bytes</p>`;
    }
});
</script>
```

## 说明
### 常见问题
1. **文件选择限制**: 使用`multiple`属性可以允许用户选择多个文件。如果未设置该属性，FileList将只包含一个文件。
2. **支持的浏览器**: FileList在大多数现代浏览器中得到支持，但在某些老旧版本的浏览器中可能存在兼容性问题。
3. **只读特性**: FileList对象是只读的，无法直接修改。如果需要更改文件列表，必须通过文件输入控件重新选择文件。

## 一句话总结
FileList是一个只读的文件集合，允许开发者方便地访问用户选择的多个文件的信息。