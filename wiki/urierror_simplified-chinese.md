<!--
Meta Description: # JavaScript 中的 URIError：详解与示例 ## 摘要 URIError 是 JavaScript 中的内置错误对象，表示在进行 URI 操作时发生了错误，通常在使用全局函数 decodeURI() 或 decodeURIComponent() 处理不正确的 URI 时引发。 ##...
Meta Keywords: urierror, uri, javascript, decodeuricomponent, message
-->

# JavaScript 中的 URIError：详解与示例

## 摘要
URIError 是 JavaScript 中的内置错误对象，表示在进行 URI 操作时发生了错误，通常在使用全局函数 decodeURI() 或 decodeURIComponent() 处理不正确的 URI 时引发。

## 文档
### 目的
URIError 主要用于捕获 URI（统一资源标识符）处理中的错误，确保开发者能够识别并处理这些错误，从而提高代码的健壮性。

### 使用方法
当使用 decodeURI() 或 decodeURIComponent() 函数时，如果传入的字符串不是有效的 URI，JavaScript 将抛出 URIError。例如，未转义的字符（如 `%` 后面没有有效的十六进制数字）会导致 URIError 被抛出。

### 详细信息
- **构造函数**：URIError 是内置错误对象的一种，构造函数为 `URIError(message)`。
- **属性**：URIError 继承自 Error 对象，具有以下属性：
  - `name`：返回错误的名称，URIError。
  - `message`：一个描述错误的字符串。

## 示例
### 基本用法
以下是一个引发 URIError 的示例代码：

```javascript
try {
    decodeURIComponent('%');
} catch (e) {
    if (e instanceof URIError) {
        console.log('捕获到 URIError：', e.message);
    }
}
```

在这个示例中，`decodeURIComponent('%')` 将引发 URIError，因为 `%` 后面没有有效的十六进制数字。

### 正确使用示例
以下是一个有效的 URI 解码示例：

```javascript
try {
    const decoded = decodeURIComponent('%E4%BD%A0%E5%A5%BD'); // '你好'
    console.log(decoded);
} catch (e) {
    console.error('解码错误：', e.message);
}
```

在这个例子中，`decodeURIComponent` 被正确地调用，返回了有效的中文字符。

## 解释
### 常见问题与注意事项
- **无效输入**：确保输入给 `decodeURI` 和 `decodeURIComponent` 的字符串是有效的 URI。无效输入将导致 URIError。
- **调试**：在捕获 URIError 时，可以通过 `e.message` 获取具体的错误信息，有助于调试。
- **兼容性**：URIError 在所有现代浏览器和 JavaScript 环境中均得到支持。

## 一句话总结
URIError 是 JavaScript 中用于表示 URI 操作错误的内置错误对象，通常在处理无效 URI 时抛出。