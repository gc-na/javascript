<!--
Meta Description: # PerformanceObserver: JavaScript 性能监测的强大工具 ## 概述 `PerformanceObserver` 是一个用于监测和记录性能指标的 JavaScript 接口，帮助开发者获取网页性能数据，以便优化应用程序性能。 ## 文档 ### 目的 `Performa...
Meta Keywords: performanceobserver, entry, javascript, mark, measure
-->

# PerformanceObserver: JavaScript 性能监测的强大工具

## 概述
`PerformanceObserver` 是一个用于监测和记录性能指标的 JavaScript 接口，帮助开发者获取网页性能数据，以便优化应用程序性能。

## 文档

### 目的
`PerformanceObserver` 允许开发者异步地观察性能相关的事件，如资源加载时间、用户交互的延迟等。通过使用这个接口，开发者可以实时收集并处理性能数据，进而优化网页性能。

### 用法
要使用 `PerformanceObserver`，需要按照以下步骤进行：

1. 创建 `PerformanceObserver` 实例，并提供一个回调函数，处理性能条目。
2. 指定要观察的性能条目类型，如 `resource`, `mark`, `measure` 等。
3. 调用 `observe` 方法开始观察。

### 详细信息
- **构造函数**: `PerformanceObserver(callback)`
  - `callback`: 当观察到指定类型的性能条目时调用的函数。

- **方法**:
  - `observe(options)`: 开始观察指定类型的性能条目。
    - `options` 对象可以包含以下属性：
      - `type`: 要观察的性能条目类型（如 `mark`, `measure`, `resource`）。
      - `buffered`: 布尔值，指示是否包括已记录的性能条目。

- **示例**: 
  ```javascript
  const observer = new PerformanceObserver((list) => {
      list.getEntries().forEach((entry) => {
          console.log(`${entry.name} took ${entry.duration} ms`);
      });
  });

  observer.observe({ entryTypes: ['measure'] });

  performance.mark('start');
// 进行一些操作
  performance.mark('end');
  performance.measure('myMeasure', 'start', 'end');
  ```

## 示例
以下是一个简单的示例，展示如何使用 `PerformanceObserver`：

### 监测资源加载时间
```javascript
const resourceObserver = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`资源 ${entry.name} 加载耗时 ${entry.duration} ms`);
    });
});

resourceObserver.observe({ entryTypes: ['resource'] });
```

## 说明
- **常见问题**:
  - 确保在页面上有实际的性能条目可供观察，否则回调函数可能不会被调用。
  - `PerformanceObserver` 在某些旧版本的浏览器中可能不受支持，检查兼容性是很重要的。

- **注意事项**:
  - 使用 `PerformanceObserver` 时，应该合理设计性能数据的处理逻辑，避免过多的计算影响性能。
  - 在不再需要观察时，建议使用 `disconnect()` 方法停止观察，以释放资源。

## 一句话总结
`PerformanceObserver` 是一个强大的工具，用于异步监测和记录网页性能数据，帮助开发者优化应用程序性能。