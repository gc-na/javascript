<!--
Meta Description: # JavaScript onstorage 事件详解 ## 概述 `onstorage` 事件是一个用于监听 Web Storage API 中 `localStorage` 和 `sessionStorage` 变化的事件。当存储在同一来源的不同窗口或标签页之间发生变化时，`onstorage`...
Meta Keywords: onstorage, event, localstorage, storage, sessionstorage
-->

# JavaScript onstorage 事件详解

## 概述
`onstorage` 事件是一个用于监听 Web Storage API 中 `localStorage` 和 `sessionStorage` 变化的事件。当存储在同一来源的不同窗口或标签页之间发生变化时，`onstorage` 事件会被触发。

## 文档
### 目的
`onstorage` 事件的主要目的是在多个浏览器窗口或标签页中同步数据。当使用 `localStorage` 或 `sessionStorage` 进行数据存储时，任何窗口或标签页的更改都会通过此事件通知其他窗口或标签页。

### 用法
`onstorage` 事件可以通过为 `window` 对象添加事件监听器来使用。事件处理程序会接收一个 `StorageEvent` 对象，包含关于变化的信息。

```javascript
window.addEventListener('storage', function(event) {
    console.log('Storage key changed:', event.key);
    console.log('New value:', event.newValue);
    console.log('Old value:', event.oldValue);
});
```

### 事件属性
- `key`：被更改的存储项的键名。
- `newValue`：更改后的值。
- `oldValue`：更改前的值。
- `url`：触发事件的页面的 URL。
- `storageArea`：发生变化的存储区域（通常为 `localStorage` 或 `sessionStorage`）。

## 示例
### 示例 1：基本用法
```javascript
// 在一个窗口中设置 localStorage
localStorage.setItem('username', 'Alice');

// 在另一个窗口中监听
window.addEventListener('storage', function(event) {
    console.log('Username changed to:', event.newValue);
});
```

### 示例 2：多窗口同步
```javascript
// 窗口1
function updateStorage() {
    localStorage.setItem('counter', (parseInt(localStorage.getItem('counter')) || 0) + 1);
}

// 窗口2
window.addEventListener('storage', function(event) {
    if (event.key === 'counter') {
        console.log('Counter updated: ', event.newValue);
    }
});
```

## 说明
### 常见问题
1. **事件不触发**：`onstorage` 事件仅在不同的窗口或标签页中触发，而在同一窗口中触发的更改不会引发该事件。
2. **sessionStorage 不触发**：`sessionStorage` 的变化不会引发 `onstorage` 事件，只会在同一窗口中有效。
3. **跨源限制**：`onstorage` 事件只能在相同来源（协议、主机和端口）之间触发。

## 一句话总结
`onstorage` 事件用于监听 Web Storage 中的数据变化，帮助实现多窗口或标签页的数据同步。