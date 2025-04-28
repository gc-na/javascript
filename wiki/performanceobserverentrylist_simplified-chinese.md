<!--
Meta Description: # PerformanceObserverEntryList：JavaScript 性能观察器条目列表 ## 摘要 `PerformanceObserverEntryList` 是 JavaScript 中的一种数据结构，用于存储由 `PerformanceObserver` 收集的性能条目。这些条...
Meta Keywords: performanceobserverentrylist, performanceobserver, measure, javascript, 当性能条目被记录时
-->

# PerformanceObserverEntryList：JavaScript 性能观察器条目列表

## 摘要
`PerformanceObserverEntryList` 是 JavaScript 中的一种数据结构，用于存储由 `PerformanceObserver` 收集的性能条目。这些条目包含关于页面性能的详细信息，帮助开发者优化应用程序的性能。

## 文档
`PerformanceObserverEntryList` 是一个接口，提供了对多个性能条目的访问。这些性能条目是通过性能观察器收集的，主要用于监控和分析网页的性能。使用 `PerformanceObserver` 时，你可以注册一个回调函数来接收性能条目，并通过 `PerformanceObserverEntryList` 来访问这些条目。

### 目的
`PerformanceObserverEntryList` 旨在提供一种方便的方式来访问多个性能条目，便于开发者分析和优化应用程序性能。

### 使用
要使用 `PerformanceObserverEntryList`，你首先需要创建一个 `PerformanceObserver` 实例，并指定一个回调函数。当性能条目被记录时，这个回调函数会被调用。回调函数的参数是一个 `PerformanceObserver` 对象，你可以通过它来访问 `PerformanceObserverEntryList`。

### 详细信息
- `PerformanceObserverEntryList` 的主要方法包括：
  - `getEntries()`：返回所有性能条目。
  - `getEntriesByName(name)`：根据条目名称返回性能条目。
  - `getEntriesByType(type)`：根据条目类型返回性能条目。
  
这些方法使得开发者能够根据需求筛选和获取所需的性能数据。

## 示例
以下是使用 `PerformanceObserverEntryList` 的基本示例：

```javascript
// 创建一个 PerformanceObserver 实例
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  console.log(entries);
});

// 开始观察某种性能条目
observer.observe({ entryTypes: ['measure'] });

// 记录一些性能测量
performance.measure('My Measure', 'startMark', 'endMark');
```

在这个示例中，我们创建了一个性能观察器，并观察类型为 “measure” 的性能条目。当性能条目被记录时，回调函数将打印出所有性能条目。

## 解释
使用 `PerformanceObserverEntryList` 时的常见问题包括：
- 确保在性能条目被生成之前调用 `observe` 方法，这样才能捕获到所有条目。
- 了解不同性能条目的类型（如 `mark`、`measure` 等），以便正确使用 `getEntriesByType()` 方法。
- 注意性能条目的生命周期，确保在适当的时机处理这些数据，以免数据丢失。

## 一句总结
`PerformanceObserverEntryList` 是一个用于存储和访问性能观察器收集的性能条目的接口，帮助开发者优化网页性能。