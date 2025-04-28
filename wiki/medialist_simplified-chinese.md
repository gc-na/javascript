<!--
Meta Description: # MediaList: JavaScript 的媒体列表接口 ## 摘要 `MediaList` 是一个用于管理和操作 CSS 媒体查询列表的接口，允许开发者在 JavaScript 中动态访问和修改样式表的媒体查询。 ## 文档 `MediaList` 接口提供了一系列方法和属性，用于处理文档中...
Meta Keywords: medialist, javascript, let, length, stylesheet
-->

# MediaList: JavaScript 的媒体列表接口

## 摘要
`MediaList` 是一个用于管理和操作 CSS 媒体查询列表的接口，允许开发者在 JavaScript 中动态访问和修改样式表的媒体查询。

## 文档
`MediaList` 接口提供了一系列方法和属性，用于处理文档中的媒体查询。它通常用于与 CSS 样式表相关的操作，主要用于获取和更新媒体条件。每个样式表都有一个 `MediaList` 对象，您可以通过 `CSSStyleSheet` 接口访问。

### 主要属性
- `length`: 返回媒体查询列表中的媒体查询数量。
- `media`: 返回当前 `MediaList` 的媒体条件。
  
### 主要方法
- `item(index)`: 返回指定索引位置的媒体查询。
- `appendMedium(medium)`: 向媒体列表中添加新的媒体条件。
- `deleteMedium(medium)`: 从媒体列表中删除指定的媒体条件。

## 示例
下面是一些基本的使用示例，展示如何使用 `MediaList` 接口：

### 示例 1: 访问和输出媒体查询
```javascript
let styleSheet = document.styleSheets[0]; // 获取第一个样式表
let mediaList = styleSheet.media; // 获取该样式表的 MediaList

console.log(mediaList.length); // 输出媒体查询数量

for (let i = 0; i < mediaList.length; i++) {
    console.log(mediaList.item(i)); // 输出每个媒体查询
}
```

### 示例 2: 添加和删除媒体条件
```javascript
let styleSheet = document.styleSheets[0];
let mediaList = styleSheet.media;

mediaList.appendMedium('screen and (max-width: 600px)'); // 添加新的媒体查询
console.log(mediaList); // 输出更新后的媒体查询列表

mediaList.deleteMedium('screen and (max-width: 600px)'); // 删除刚添加的媒体查询
console.log(mediaList); // 输出更新后的媒体查询列表
```

## 解释
在使用 `MediaList` 时，开发者可能会遇到一些常见问题：

- **索引超出范围**: 使用 `item()` 方法时，如果索引超出范围，将返回 `null`，因此在访问媒体查询前应检查 `length` 属性。
- **不可变性**: 注意不是所有的样式表都允许修改其媒体列表。如果样式表是来自外部文件且被标记为只读，尝试修改将会失败。
- **异步加载**: 如果样式表是动态加载的，确保在样式表加载完成后再访问其 `MediaList`。

## 一句话总结
`MediaList` 是 JavaScript 中用于动态管理和操作 CSS 媒体查询列表的接口。