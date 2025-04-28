<!--
Meta Description: # JavaScript 存储（Storage）详解 ## 简介 JavaScript 存储是指在客户端（浏览器）中保存数据的能力，主要通过 Web Storage API 实现，包括 Local Storage 和 Session Storage。这使得开发者能够在用户的浏览器中保存和访问数据，以...
Meta Keywords: storage, local, session, javascript, localstorage
-->

# JavaScript 存储（Storage）详解

## 简介
JavaScript 存储是指在客户端（浏览器）中保存数据的能力，主要通过 Web Storage API 实现，包括 Local Storage 和 Session Storage。这使得开发者能够在用户的浏览器中保存和访问数据，以提供更好的用户体验。

## 文档
### 目的
JavaScript 存储提供了一种简单的方法来存储键值对数据，允许开发者在用户的浏览器中持久化数据。Local Storage 用于长久存储数据，而 Session Storage 则用于会话期间的存储。

### 使用
- **Local Storage**: 数据在浏览器关闭后仍然存在，适合用于保存用户的偏好设置。
- **Session Storage**: 数据在浏览器标签页关闭后消失，适合用于临时数据保存，如表单数据。

#### API 方法
1. `setItem(key, value)`: 存储数据。
2. `getItem(key)`: 获取存储的数据。
3. `removeItem(key)`: 移除指定的存储项。
4. `clear()`: 清空所有存储数据。
5. `length`: 获取存储项的数量。

### 详细说明
- Local Storage 和 Session Storage 的数据存储在同一域下，且大小限制通常为 5MB。
- 存储的数据必须是字符串类型，因此可以使用 `JSON.stringify()` 和 `JSON.parse()` 方法来存储和读取对象。
- Local Storage 的数据在不同的浏览器窗口和标签页中是共享的，而 Session Storage 则不共享。

## 示例
```javascript
// 使用 Local Storage
localStorage.setItem('username', 'JohnDoe');
console.log(localStorage.getItem('username')); // 输出: JohnDoe

// 使用 Session Storage
sessionStorage.setItem('sessionID', 'abc123');
console.log(sessionStorage.getItem('sessionID')); // 输出: abc123

// 移除项
localStorage.removeItem('username');

// 清空所有
localStorage.clear();
```

## 说明
- **常见问题**: 
  - Local Storage 和 Session Storage 不支持存储对象，需先转换为字符串。
  - 同源策略限制了跨域访问存储数据的能力。
- **注意事项**: 
  - 避免存储敏感信息，如密码，因为数据以明文形式存储。
  - 当存储量超过限制时，浏览器会抛出错误。

## 一句话总结
JavaScript 存储通过 Local Storage 和 Session Storage 提供了在客户端持久化和临时存储数据的能力。