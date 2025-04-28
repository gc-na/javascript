<!--
Meta Description: # onwheel 事件在 JavaScript 中的应用 ## 摘要 `onwheel` 是一个 JavaScript 事件，用于处理用户在页面上滚动鼠标滚轮或触控板时的交互。该事件提供了更精确的控制，允许开发者捕捉和响应滚轮滚动的行为。 ## 文档 `onwheel` 事件是现代浏览器中引入的，...
Meta Keywords: onwheel, event, javascript, deltay, function
-->

# onwheel 事件在 JavaScript 中的应用

## 摘要
`onwheel` 是一个 JavaScript 事件，用于处理用户在页面上滚动鼠标滚轮或触控板时的交互。该事件提供了更精确的控制，允许开发者捕捉和响应滚轮滚动的行为。

## 文档
`onwheel` 事件是现代浏览器中引入的，旨在替代旧版的 `mousewheel` 事件。与 `mousewheel` 不同，`onwheel` 提供了标准化的事件属性，使得开发者能够更容易地处理不同设备上的滚动行为。该事件的主要目的是捕获鼠标滚轮的滚动和触控板的滑动。

### 目的
`onwheel` 事件用于监测用户的滚动动作，提供了一个简单的方法来实现平滑滚动、无限滚动列表或自定义滚动行为。

### 使用
在 JavaScript 中，可以通过以下方式添加 `onwheel` 事件监听器：

```javascript
element.onwheel = function(event) {
    // 处理滚轮事件
    console.log(event.deltaY); // 获取滚动距离
};
```

或使用 `addEventListener` 方法：

```javascript
element.addEventListener('wheel', function(event) {
    // 处理滚轮事件
    console.log(event.deltaY); // 获取滚动距离
});
```

### 事件属性
- `deltaX`：表示水平方向的滚动量。
- `deltaY`：表示垂直方向的滚动量。
- `deltaZ`：表示第三个维度（通常为 0）。
- `deltaMode`：指示 `deltaX`、`deltaY` 和 `deltaZ` 的单位（像素、行或页）。

## 示例
### 示例 1：基本用法
```html
<div id="scrollable" style="height: 200px; overflow: auto;">
    <!-- 这里是内容 -->
</div>

<script>
    const scrollable = document.getElementById('scrollable');

    scrollable.onwheel = function(event) {
        console.log('滚动量（Y轴）:', event.deltaY);
    };
</script>
```

### 示例 2：自定义滚动行为
```javascript
document.addEventListener('wheel', function(event) {
    event.preventDefault(); // 阻止默认滚动
    window.scrollBy(0, event.deltaY); // 自定义滚动
});
```

## 说明
- 在某些浏览器中，`onwheel` 事件可能不支持，建议开发者使用 `addEventListener` 方法来保证兼容性。
- 注意 `event.preventDefault()` 的使用，以避免干扰默认的滚动行为。
- `deltaY` 的值可以是正数或负数，正数表示向下滚动，负数表示向上滚动。

## 一句话总结
`onwheel` 事件在 JavaScript 中用于捕捉用户的滚轮滚动动作，提供了强大的滚动交互控制。