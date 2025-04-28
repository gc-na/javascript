<!--
Meta Description: # PerformanceMark：JavaScript 性能标记的全面指南 ## 概要 PerformanceMark 是一个 JavaScript API，用于定义和测量代码执行的特定点，以帮助开发者分析性能并优化应用程序的响应速度。 ## 文档 ### 目的 PerformanceMark 旨...
Meta Keywords: performancemark, performance, mark, javascript, api
-->

# PerformanceMark：JavaScript 性能标记的全面指南

## 概要
PerformanceMark 是一个 JavaScript API，用于定义和测量代码执行的特定点，以帮助开发者分析性能并优化应用程序的响应速度。

## 文档
### 目的
PerformanceMark 旨在提供一种简单的方式来标记代码的执行点，从而使开发者能够在浏览器的性能分析工具中查看这些标记，进而识别性能瓶颈。

### 用法
要使用 PerformanceMark，您可以调用 `performance.mark()` 方法并传入一个字符串作为标记的名称。这个标记将被添加到浏览器的性能时间线中，便于后续的性能分析。

#### 语法
```javascript
performance.mark(markName);
```
- **markName**: 一个字符串，表示标记的名称。

### 详细信息
- 每个标记都是一个时间戳，记录了调用 `performance.mark()` 时的时间。
- 不同的标记可以通过名称进行区分，开发者可以根据需求在代码中的多个位置调用此方法。
- 标记信息可以通过 `performance.getEntriesByType('mark')` 获取，便于进一步分析。

## 示例
以下是如何使用 PerformanceMark 的基本示例：

```javascript
// 在代码的开始位置标记
performance.mark('start');

// 执行一些操作
doSomeHeavyTask();

// 在操作结束后标记
performance.mark('end');

// 获取所有标记
const marks = performance.getEntriesByType('mark');
console.log(marks);
```

## 说明
- **常见陷阱**: 确保标记名称是唯一的，以避免不同操作的标记混淆。
- **注意事项**: 在浏览器的开发者工具中查看性能标记时，确保已经打开性能分析面板，以便能看到标记的时间线。
- **性能影响**: 虽然 PerformanceMark 本身的开销很小，但频繁调用可能会对性能分析结果产生影响，因此应合理使用。

## 一句话总结
PerformanceMark 是 JavaScript 中的一个 API，用于在代码执行时创建性能标记，以帮助开发者分析和优化应用程序性能。