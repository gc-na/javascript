<!--
Meta Description: # ScreenOrientation：JavaScript 的螢幕方向 API ## 概述 ScreenOrientation 是一個 JavaScript API，用於查詢和控制設備的螢幕方向。這個功能在開發響應式和適配不同設備的網頁應用時特別重要，因為它可以幫助開發者為用戶提供更佳的使用體驗。...
Meta Keywords: screen, orientation, screenorientation, javascript, api
-->

# ScreenOrientation：JavaScript 的螢幕方向 API

## 概述
ScreenOrientation 是一個 JavaScript API，用於查詢和控制設備的螢幕方向。這個功能在開發響應式和適配不同設備的網頁應用時特別重要，因為它可以幫助開發者為用戶提供更佳的使用體驗。

## 文檔
### 目的
ScreenOrientation API 允許開發者獲取當前螢幕方向以及設置螢幕方向，這對於設計遊戲、視頻播放或需要特定方向的應用非常有用。它可以幫助開發者根據設備的方向變化調整界面布局。

### 用法
要使用 ScreenOrientation API，首先需要檢查瀏覽器是否支持它。然後可以使用 `screen.orientation` 屬性來獲取當前的螢幕方向，並使用 `screen.orientation.lock()` 來鎖定螢幕方向。

#### 獲取當前螢幕方向
```javascript
if (screen.orientation) {
    console.log(screen.orientation.type); // 輸出: "portrait-primary" 或 "landscape-primary"
}
```

#### 鎖定螢幕方向
```javascript
function lockOrientation() {
    if (screen.orientation && screen.orientation.lock) {
        screen.orientation.lock('portrait').then(function() {
            console.log('螢幕方向已鎖定為豎屏');
        }).catch(function(error) {
            console.error('鎖定螢幕方向失敗:', error);
        });
    }
}
```

#### 解鎖螢幕方向
```javascript
function unlockOrientation() {
    if (screen.orientation && screen.orientation.unlock) {
        screen.orientation.unlock();
        console.log('螢幕方向已解鎖');
    }
}
```

## 示例
### 基本用法
以下示例展示了一個簡單的網頁應用，當使用者點擊按鈕時，會鎖定螢幕方向為豎屏。
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>ScreenOrientation 示例</title>
</head>
<body>
    <button onclick="lockOrientation()">鎖定豎屏</button>
    <button onclick="unlockOrientation()">解鎖方向</button>
    <script>
        // 上述 JavaScript 代碼
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **不支持的環境**：並非所有瀏覽器或設備都支持 ScreenOrientation API，開發者需要在使用前進行檢查。
- **權限問題**：某些操作（例如鎖定方向）可能需要用戶的授權或特定的上下文（如全螢幕模式）。
- **錯誤處理**：在鎖定或解鎖方向時，務必要添加錯誤處理，因為這些操作可能會失敗，尤其是在不支持的設備上。

## 一句總結
ScreenOrientation API 是一個強大的工具，幫助開發者在 JavaScript 中控制和查詢設備的螢幕方向。