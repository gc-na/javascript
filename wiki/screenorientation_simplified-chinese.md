<!--
Meta Description: # ScreenOrientation：JavaScript 屏幕方向 API ## 概述 `ScreenOrientation` 是一个 JavaScript API，用于获取和控制设备的屏幕方向，允许开发者根据设备的方向变化来优化用户体验。 ## 文档 ### 目的 `ScreenOrienta...
Meta Keywords: screenorientation, orientation, api, console, error
-->

# ScreenOrientation：JavaScript 屏幕方向 API

## 概述
`ScreenOrientation` 是一个 JavaScript API，用于获取和控制设备的屏幕方向，允许开发者根据设备的方向变化来优化用户体验。

## 文档
### 目的
`ScreenOrientation` API 旨在提供一种简单的方式来访问和修改设备的屏幕方向，支持网页开发者创建响应式设计，适配不同的设备和方向。

### 使用方法
`ScreenOrientation` 接口可以通过 `window.screen.orientation` 访问。该接口提供了几个重要的方法和属性：

- **属性：**
  - `type`：返回当前屏幕方向的类型（如 `portrait-primary`、`landscape-secondary`）。
  - `angle`：返回当前屏幕的旋转角度（0、90、180、270）。

- **方法：**
  - `lock(orientation)`：请求锁定屏幕方向，参数为希望锁定的方向（如 `portrait`、`landscape`）。
  - `unlock()`：解锁屏幕方向，恢复默认设置。

### 示例
以下是使用 `ScreenOrientation` API 的基本示例：

```javascript
// 获取当前屏幕方向
const orientation = screen.orientation;

// 输出当前类型和角度
console.log(`当前方向类型: ${orientation.type}`);
console.log(`当前角度: ${orientation.angle}`);

// 锁定屏幕方向为横屏
orientation.lock('landscape').then(() => {
    console.log('屏幕已锁定为横屏方向');
}).catch((error) => {
    console.error('锁定方向失败:', error);
});

// 解锁屏幕方向
orientation.unlock().then(() => {
    console.log('屏幕方向已解锁');
}).catch((error) => {
    console.error('解锁方向失败:', error);
});
```

### 说明
在使用 `ScreenOrientation` API 时，开发者应注意以下事项：

- **兼容性**：并非所有浏览器都支持 `ScreenOrientation` API，使用前请检查兼容性。
- **权限**：某些浏览器可能需要用户授权才能锁定屏幕方向。
- **错误处理**：在调用 `lock()` 和 `unlock()` 方法时，确保实现适当的错误处理，避免用户体验受损。

## 一句总结
`ScreenOrientation` API 提供了便捷的方式来获取和控制设备的屏幕方向，优化网页在不同设备上的展示效果。