<!--
Meta Description: # CookieStore：JavaScript 中的 Cookie 存储 API ## 概述 CookieStore 是一个 JavaScript API，用于管理和操作浏览器的 Cookie。它提供了一种简单的方法来读取、添加、更新和删除 Cookie，在现代 Web 开发中非常重要。 ## 文...
Meta Keywords: cookie, cookiestore, name, javascript, api
-->

# CookieStore：JavaScript 中的 Cookie 存储 API

## 概述
CookieStore 是一个 JavaScript API，用于管理和操作浏览器的 Cookie。它提供了一种简单的方法来读取、添加、更新和删除 Cookie，在现代 Web 开发中非常重要。

## 文档
### 目的
CookieStore API 旨在简化 Cookie 的处理，使开发者能够在客户端更轻松地管理用户会话、偏好设置和其他重要数据。

### 使用
CookieStore 提供以下主要方法：
- `getAll()`: 获取当前域下的所有 Cookie。
- `get(name)`: 根据名称获取特定的 Cookie。
- `set(cookie)`: 添加或更新一个 Cookie。
- `delete(name)`: 删除指定名称的 Cookie。

### 详细说明
CookieStore API 的设计遵循现代 Web 开发标准，以保证其兼容性和易用性。所有操作均为异步执行，返回 Promise 对象，确保在处理 Cookie 时不会阻塞主线程。

## 示例
### 示例 1：获取所有 Cookie
```javascript
async function fetchAllCookies() {
    const cookies = await cookieStore.getAll();
    console.log(cookies);
}
fetchAllCookies();
```

### 示例 2：获取特定 Cookie
```javascript
async function fetchCookie(name) {
    const cookie = await cookieStore.get(name);
    console.log(cookie);
}
fetchCookie('session_id');
```

### 示例 3：设置 Cookie
```javascript
async function setCookie() {
    await cookieStore.set({
        name: 'user_preference',
        value: 'dark_mode',
        expires: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000), // 7天后过期
        path: '/',
        sameSite: 'Lax'
    });
}
setCookie();
```

### 示例 4：删除 Cookie
```javascript
async function deleteCookie(name) {
    await cookieStore.delete(name);
    console.log(`${name} cookie has been deleted.`);
}
deleteCookie('user_preference');
```

## 说明
使用 CookieStore API 时，开发者需注意以下几点：
- Cookie 的大小限制：每个 Cookie 不应超过 4KB，且每个域名下的 Cookie 数量有限制（通常为 20 个）。
- 过期时间：设置 Cookie 时，应明确指定过期时间，否则 Cookie 将在浏览器会话结束时删除。
- 跨域访问：Cookie 的读取和写入受同源策略限制，确保在合适的域名下操作。

## 一句话总结
CookieStore 是一个便捷的 JavaScript API，用于有效管理浏览器中的 Cookie。