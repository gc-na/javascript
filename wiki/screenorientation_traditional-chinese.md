<!--
Meta Description: # ScreenOrientation 在 JavaScript 中的應用 ## 簡介 `ScreenOrientation` 是一個 Web API，允許開發者檢測和控制設備的螢幕方向。它能夠提供更好的用戶體驗，特別是在移動設備上，通過動態地調整介面以適應不同的螢幕方向。 ## 文檔 ### 目的...
Meta Keywords: screenorientation, orientation, screen, api, javascript
-->

# ScreenOrientation 在 JavaScript 中的應用

## 簡介
`ScreenOrientation` 是一個 Web API，允許開發者檢測和控制設備的螢幕方向。它能夠提供更好的用戶體驗，特別是在移動設備上，通過動態地調整介面以適應不同的螢幕方向。

## 文檔
### 目的
`ScreenOrientation` API 的主要目的是讓開發者能夠獲取和設置設備螢幕的方向，從而優化應用程式的顯示效果。

### 使用方法
要使用 `ScreenOrientation`，首先需要訪問 `screen.orientation` 屬性。該屬性返回一個 `ScreenOrientation` 物件，該物件提供了多種方法和屬性來控制螢幕方向。

#### 主要屬性
- `type`: 返回當前的螢幕方向類型（如 `portrait-primary`, `landscape-primary` 等）。
- `angle`: 返回當前螢幕旋轉的角度（0, 90, 180, 270）。

#### 主要方法
- `lock(orientation)`: 鎖定螢幕方向。
- `unlock()`: 解鎖螢幕方向，恢復用戶的控制。

### 示例
以下是一些基本的使用示例，展示如何使用 `ScreenOrientation` API。

#### 獲取當前螢幕方向
```javascript
if (screen.orientation) {
    console.log("當前螢幕方向:", screen.orientation.type);
}
```

#### 鎖定螢幕方向為橫向
```javascript
if (screen.orientation) {
    screen.orientation.lock('landscape').then(() => {
        console.log("成功鎖定為橫向模式");
    }).catch((error) => {
        console.error("無法鎖定螢幕方向:", error);
    });
}
```

#### 解鎖螢幕方向
```javascript
if (screen.orientation) {
    screen.orientation.unlock();
    console.log("螢幕方向已解鎖");
}
```

## 解釋
### 常見陷阱
1. **不支持的瀏覽器**: 並非所有瀏覽器都支持 `ScreenOrientation` API，因此在使用前請檢查瀏覽器兼容性。
2. **使用權限**: 鎖定螢幕方向可能需要用戶授權，特別是在某些移動設備上。
3. **異步操作**: `lock()` 方法是異步的，因此需要使用 `.then()` 和 `.catch()` 來處理返回的 Promise。

### 附加注意事項
- 確保在 `DOMContentLoaded` 事件後使用 `ScreenOrientation` 以確保 DOM 已完全加載。
- 監聽 `screen.orientation.change` 事件，以便在螢幕方向改變時進行相應處理。

## 一句總結
`ScreenOrientation` API 讓開發者能夠靈活地控制和檢測設備的螢幕方向，從而提升用戶的交互體驗。