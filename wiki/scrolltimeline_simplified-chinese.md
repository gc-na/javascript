<!--
Meta Description: # ScrollTimeline：JavaScript中的滚动时间轴功能 ## 简介 ScrollTimeline 是一种新引入的JavaScript API，旨在帮助开发者在用户滚动页面时创建更具动态感和沉浸感的动画效果。此API使得开发者能够基于用户的滚动位置控制动画的时间进度，提升用户体验。 ...
Meta Keywords: scrolltimeline, scrollsource, div, const, document
-->

# ScrollTimeline：JavaScript中的滚动时间轴功能

## 简介
ScrollTimeline 是一种新引入的JavaScript API，旨在帮助开发者在用户滚动页面时创建更具动态感和沉浸感的动画效果。此API使得开发者能够基于用户的滚动位置控制动画的时间进度，提升用户体验。

## 文档
### 目的
ScrollTimeline 允许开发者通过滚动事件来驱动动画的执行，从而为网站提供更加流畅和直观的交互体验。它为创建与用户滚动行为直接相关的动画提供了强大的工具。

### 使用方法
在使用 ScrollTimeline 之前，开发者需要确保浏览器支持该功能。以下是基本的使用步骤：

1. **创建 ScrollTimeline 实例**：
   通过 `ScrollTimeline` 构造函数创建一个新的滚动时间轴实例。

   ```javascript
   const scrollTimeline = new ScrollTimeline({
       scrollSource: document.querySelector('#scroll-container'), // 滚动源
       timeRange: 1000 // 时间范围（以像素为单位）
   });
   ```

2. **将 ScrollTimeline 应用到动画上**：
   使用 CSS 动画和关键帧将滚动时间轴与特定动画关联。

   ```css
   @keyframes myAnimation {
       from {
           opacity: 0;
       }
       to {
           opacity: 1;
       }
   }

   .animated-element {
       animation: myAnimation 1s forwards;
       animation-timeline: scrollTimeline; // 关联到 ScrollTimeline
   }
   ```

3. **触发动画**：
   一旦用户开始滚动，定义好的动画将会根据滚动的深度和速度进行触发。

### 详细信息
- **scrollSource**：指定滚动事件源的DOM元素。
- **timeRange**：控制动画的时间范围，以像素为单位设定滚动的阈值。
- **animation-timeline**：将 ScrollTimeline 实例应用到特定的CSS动画上。

## 示例
以下是一个简单的 ScrollTimeline 使用示例：

```html
<div id="scroll-container" style="height: 200vh;">
    <div class="animated-element" style="position:fixed; top: 50%; left: 50%;">
        滚动我
    </div>
</div>

<script>
   const scrollTimeline = new ScrollTimeline({
       scrollSource: document.querySelector('#scroll-container'),
       timeRange: 1000
   });

   const animatedElement = document.querySelector('.animated-element');
   animatedElement.style.animationTimeline = scrollTimeline;
</script>
```

## 说明
- **常见陷阱**：确保正确指定 `scrollSource`，否则滚动事件将不会触发动画。
- **兼容性**：ScrollTimeline 在某些老旧浏览器上可能不被支持，开发者应考虑使用适当的降级策略。
- **性能**：过多的动画和复杂的计算可能影响性能，建议在使用时进行性能测试。
  
## 一句话总结
ScrollTimeline 是一个强大的JavaScript API，允许开发者创建基于用户滚动的动态动画效果。