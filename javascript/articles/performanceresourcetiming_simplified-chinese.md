<!--
Meta Description: # PerformanceResourceTiming：JavaScript 性能资源计时 API ## 概述 `PerformanceResourceTiming` 是一个用于获取并分析网络资源性能的 JavaScript API。它提供了关于网络请求（如图像、脚本和样式表）的详细信息，有助于开发...
Meta Keywords: resource, performanceresourcetiming, console, log, javascript
-->

# PerformanceResourceTiming：JavaScript 性能资源计时 API

## 概述
`PerformanceResourceTiming` 是一个用于获取并分析网络资源性能的 JavaScript API。它提供了关于网络请求（如图像、脚本和样式表）的详细信息，有助于开发者优化网页性能。

## 文档
`PerformanceResourceTiming` 接口扩展了 `PerformanceEntry` 接口，专注于表示加载资源的性能数据。它提供了一系列属性，用于跟踪资源加载的时间和各个阶段的持续时间。

### 主要属性
- `fetchStart`：请求开始的时间戳。
- `domainLookupStart`：DNS 查找开始的时间。
- `domainLookupEnd`：DNS 查找结束的时间。
- `connectStart`：TCP 连接建立的开始时间。
- `connectEnd`：TCP 连接建立的结束时间。
- `requestStart`：发送请求的时间。
- `responseStart`：接收到响应的时间。
- `responseEnd`：响应完全接收的时间。
- `duration`：资源加载的总时间。

### 用法
要获取 `PerformanceResourceTiming` 对象，开发者可以使用 `performance.getEntriesByType("resource")` 方法。此方法返回一个数组，包含所有资源的性能数据。

```javascript
const resources = performance.getEntriesByType("resource");
resources.forEach(resource => {
    console.log(`资源：${resource.name}`);
    console.log(`加载时间：${resource.duration}ms`);
});
```

## 示例
以下是一个简单的示例，演示如何使用 `PerformanceResourceTiming` 获取网页加载的资源性能信息：

```javascript
window.addEventListener("load", () => {
    const resources = performance.getEntriesByType("resource");
    resources.forEach(resource => {
        console.log(`资源名称: ${resource.name}`);
        console.log(`获取时间: ${resource.duration} ms`);
        console.log(`DNS 查找时间: ${resource.domainLookupEnd - resource.domainLookupStart} ms`);
    });
});
```

## 解释
使用 `PerformanceResourceTiming` 时，开发者应注意以下几点：

- **跨域限制**：某些跨域请求可能会由于 CORS 策略而无法获取完整的性能数据。
- **数据更新**：性能数据在页面加载后不会更新，因此确保在适当的时间点（如 `load` 事件后）收集数据。
- **浏览器支持**：虽然大多数现代浏览器支持 `PerformanceResourceTiming`，但仍需确认目标用户的浏览器兼容性。

## 一句话总结
`PerformanceResourceTiming` 是一个强大的工具，能够帮助开发者分析和优化网页资源的加载性能。