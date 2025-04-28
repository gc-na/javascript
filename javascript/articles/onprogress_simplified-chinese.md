<!--
Meta Description: # JavaScript中的onprogress事件详解 ## 概述 `onprogress`是JavaScript中一个用于处理进度事件的事件处理程序。它通常与XHR（XMLHttpRequest）对象和Fetch API一起使用，以监测文件上传和下载的进度。 ## 文档 ### 目的 `onpr...
Meta Keywords: onprogress, event, const, xhr, loaded
-->

# JavaScript中的onprogress事件详解

## 概述
`onprogress`是JavaScript中一个用于处理进度事件的事件处理程序。它通常与XHR（XMLHttpRequest）对象和Fetch API一起使用，以监测文件上传和下载的进度。

## 文档
### 目的
`onprogress`事件在进行异步操作时提供了实时的进度反馈，允许开发者根据数据传输的进度更新用户界面或执行其他逻辑。

### 使用方法
`onprogress`事件可以在多个上下文中使用，如下：

- **XMLHttpRequest**：用于监控文件上传和下载的进度。
- **Fetch API**：结合 ReadableStream 来监控数据的接收进度。

#### XMLHTTPRequest 示例
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'file-url', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`下载进度: ${percentComplete}%`);
    }
};

xhr.onload = function() {
    console.log('文件下载完成');
};

xhr.send();
```

#### Fetch API 示例
在Fetch API中，`onprogress`不直接使用，但可以通过ReadableStream实现。
```javascript
fetch('file-url')
    .then(response => {
        const reader = response.body.getReader();
        const contentLength = +response.headers.get('Content-Length');

        let loaded = 0;
        reader.read().then(function processText({ done, value }) {
            if (done) {
                console.log('文件下载完成');
                return;
            }
            loaded += value.length;
            const percentComplete = (loaded / contentLength) * 100;
            console.log(`下载进度: ${percentComplete}%`);
            return reader.read().then(processText);
        });
    });
```

## 说明
- **常见陷阱**：
  - 在使用`onprogress`时，确保`lengthComputable`属性为真，以便正确计算进度。如果该属性为假，则无法获取总长度。
  - 在XHR的`onprogress`事件中，`event.loaded`和`event.total`可能在某些情况下为0，这通常意味着不能计算进度。

- **注意事项**：
  - 仅在支持的浏览器中使用`onprogress`，某些旧版浏览器可能不完全支持该事件。
  - 对于较小的文件，进度更新可能不那么频繁，导致用户界面更新的延迟。

## 一句话总结
`onprogress`事件为JavaScript中的异步操作提供了实时进度反馈，增强了用户体验。