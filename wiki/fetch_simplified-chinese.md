<!--
Meta Description: # JavaScript Fetch API 使用指南 ## 摘要 `fetch` 是一个用于发起网络请求的 JavaScript API，提供了一个简单且灵活的方式来获取资源，并处理响应。 ## 文档 ### 目的 `fetch` API 允许开发者通过网络请求获取数据，支持 Promise 语法...
Meta Keywords: fetch, response, javascript, error, api
-->

# JavaScript Fetch API 使用指南

## 摘要
`fetch` 是一个用于发起网络请求的 JavaScript API，提供了一个简单且灵活的方式来获取资源，并处理响应。

## 文档
### 目的
`fetch` API 允许开发者通过网络请求获取数据，支持 Promise 语法，使异步操作更加简洁。它是现代 JavaScript 应用程序与服务器交互的核心工具之一。

### 用法
`fetch` 函数的基本语法如下：

```javascript
fetch(url, options)
```

- `url`: 请求的资源 URL（必需）。
- `options`: 一个可选的配置对象，可以包括 HTTP 方法、请求头、请求体等。

### 详细信息
- `fetch` 返回一个 Promise，解析为 Response 对象。
- 可以使用 `.then()` 方法处理成功的响应，使用 `.catch()` 方法处理错误。
- 支持 `GET`、`POST`、`PUT`、`DELETE` 等 HTTP 方法。

## 示例
### 基本用法
1. 发起 GET 请求：

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('网络响应错误');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('请求失败:', error));
```

2. 发起 POST 请求：

```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ key: 'value' })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('请求失败:', error));
```

## 解释
### 常见陷阱
- **CORS（跨域资源共享）**：不同源的请求可能会被浏览器拦截，需确保服务器设置了适当的 CORS 策略。
- **网络错误处理**：如果请求失败（如网络断开），Promise 会拒绝，但 HTTP 错误状态（如 404、500）不会被视为错误，需手动检查 `response.ok`。
- **响应体处理**：必须在响应之后调用正确的方法（如 `response.json()` 或 `response.text()`）来解析响应内容。

## 一句话总结
`fetch` 是 JavaScript 中用于发起网络请求的现代 API，支持 Promise，简化了数据获取和处理的流程。