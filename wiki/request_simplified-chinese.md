<!--
Meta Description: # JavaScript中的请求（Request）概述 ## 简介 在JavaScript中，请求（Request）是指通过网络向服务器发送的数据请求。它是实现客户端与服务器之间通信的关键，通常用于获取或发送数据。最常用的方式是通过XMLHttpRequest和Fetch API。 ## 文档 请求...
Meta Keywords: xhr, data, response, api, console
-->

# JavaScript中的请求（Request）概述

## 简介
在JavaScript中，请求（Request）是指通过网络向服务器发送的数据请求。它是实现客户端与服务器之间通信的关键，通常用于获取或发送数据。最常用的方式是通过XMLHttpRequest和Fetch API。

## 文档
请求的主要目的是与服务器进行数据交互。JavaScript提供了多种方法来发起请求，最常见的有以下两种：

1. **XMLHttpRequest**：这是一个较旧的API，用于在后台与服务器交换数据。它允许异步请求，从而不阻塞用户界面。
   
2. **Fetch API**：这是一个现代的API，提供了更简洁和灵活的方式来处理请求和响应。它基于Promise，使得处理异步操作更加直观。

### 使用方法
#### XMLHttpRequest
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onload = function() {
    if (xhr.status >= 200 && xhr.status < 300) {
        console.log(xhr.responseText);
    } else {
        console.error('请求失败', xhr.statusText);
    }
};
xhr.onerror = function() {
    console.error('请求错误');
};
xhr.send();
```

#### Fetch API
```javascript
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('网络响应不是OK');
        }
        return response.json();
    })
    .then(data => console.log(data))
    .catch(error => console.error('请求失败', error));
```

## 例子
### 发送GET请求
```javascript
fetch('https://api.example.com/items')
    .then(response => response.json())
    .then(data => console.log(data));
```

### 发送POST请求
```javascript
fetch('https://api.example.com/items', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ name: '新项目' })
})
.then(response => response.json())
.then(data => console.log(data));
```

## 说明
- **跨域请求**：在进行请求时，浏览器会进行同源策略限制。为了解决跨域问题，可以使用CORS（跨源资源共享）来允许不同域之间的请求。
- **错误处理**：在使用Fetch API时，如果网络错误发生，Promise会被拒绝，但HTTP错误（如404或500）不会被拒绝，需手动检查`response.ok`。
- **性能**：使用Fetch API时，建议使用`async/await`来处理异步请求，能让代码更简洁易读。

## 一句话总结
在JavaScript中，请求（Request）用于实现客户端与服务器之间的数据交互，主要通过XMLHttpRequest和Fetch API发起。