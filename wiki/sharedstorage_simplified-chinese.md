<!--
Meta Description: # SharedStorage: JavaScript 中的共享存储 ## 概述 SharedStorage 是一种新兴的 Web API，允许多个上下文（如标签页、窗口和 iframe）之间共享数据。它为跨文档的数据通信提供了一种高效的解决方案。 ## 文档 SharedStorage 的主要目的...
Meta Keywords: sharedstorage, navigator, console, log, event
-->

# SharedStorage: JavaScript 中的共享存储

## 概述
SharedStorage 是一种新兴的 Web API，允许多个上下文（如标签页、窗口和 iframe）之间共享数据。它为跨文档的数据通信提供了一种高效的解决方案。

## 文档
SharedStorage 的主要目的是通过提供一个共享的存储机制，允许不同的网页上下文之间进行数据交换。它支持字符串数据，并允许在多个上下文之间进行异步数据读取和写入。

### 主要功能
- **跨上下文共享**：多个标签页或窗口可以访问同一份数据。
- **异步操作**：读取和写入数据时不会阻塞主线程。
- **事件监听**：支持监听数据变化事件，以便实时更新。

### 使用方法
要使用 SharedStorage API，首先需要确保浏览器支持该功能。可以通过 `navigator.sharedStorage` 检查支持情况。以下是基本的使用示例：

```javascript
if ('sharedStorage' in navigator) {
    // 写入数据
    navigator.sharedStorage.setItem('key', 'value').then(() => {
        console.log('数据已写入');
    });

    // 读取数据
    navigator.sharedStorage.getItem('key').then(value => {
        console.log('获取的数据:', value);
    });

    // 监听数据变化
    navigator.sharedStorage.onstorage = (event) => {
        console.log('数据已更新:', event);
    };
} else {
    console.log('此浏览器不支持 SharedStorage');
}
```

## 示例
以下是一些使用 SharedStorage 的基本示例：

### 示例 1: 写入和读取数据
```javascript
navigator.sharedStorage.setItem('username', 'Alice').then(() => {
    return navigator.sharedStorage.getItem('username');
}).then(username => {
    console.log('当前用户:', username); // 输出: 当前用户: Alice
});
```

### 示例 2: 监听数据变化
```javascript
navigator.sharedStorage.onstorage = (event) => {
    console.log('检测到变化:', event.key, event.newValue);
};

// 在另一个上下文中更新数据
navigator.sharedStorage.setItem('username', 'Bob');
```

## 说明
使用 SharedStorage 时，开发者需注意以下几点：

- **浏览器支持**：并非所有浏览器都支持 SharedStorage，开发者应检查兼容性并提供相应的降级方案。
- **安全性**：共享存储可能会引发安全问题，如跨站请求伪造（CSRF），因此应谨慎管理存储的数据。
- **容量限制**：SharedStorage 的存储空间有限，应避免存储过多的数据，超出限制可能导致写入失败。

## 一句话总结
SharedStorage 是一个强大的 Web API，允许在多个上下文之间高效共享和同步数据。