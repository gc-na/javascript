<!--
Meta Description: # 在 JavaScript 中的 ondeviceorientation 事件 ## 簡介 `ondeviceorientation` 是一個用於捕捉設備方向變化的事件，通常用於移動設備的應用程式開發。這個事件可以幫助開發者獲取設備的方向資訊，從而在用戶互動時提供更豐富的體驗。 ## 文檔 `on...
Meta Keywords: ondeviceorientation, event, alpha, beta, gamma
-->

# 在 JavaScript 中的 ondeviceorientation 事件

## 簡介
`ondeviceorientation` 是一個用於捕捉設備方向變化的事件，通常用於移動設備的應用程式開發。這個事件可以幫助開發者獲取設備的方向資訊，從而在用戶互動時提供更豐富的體驗。

## 文檔
`ondeviceorientation` 事件會在設備的方向改變時觸發。它可以用於虛擬現實、遊戲、地圖導航等多種應用場景。當設備的方向發生變化時，開發者可以通過這個事件來獲取設備的方位角、傾斜角和旋轉角。

### 用法
要使用 `ondeviceorientation`，你需要在 JavaScript 中為 `window` 對象添加一個事件監聽器。以下是基本的用法：

```javascript
window.addEventListener("deviceorientation", function(event) {
    const alpha = event.alpha; // 繞 Z 軸的旋轉角
    const beta = event.beta;   // 繞 X 軸的傾斜角
    const gamma = event.gamma; // 繞 Y 軸的傾斜角

    console.log(`Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
});
```

### 事件物件
- `alpha`: 表示設備繞 Z 軸的旋轉角度（以度為單位）。
- `beta`: 表示設備繞 X 軸的傾斜角度（以度為單位）。
- `gamma`: 表示設備繞 Y 軸的傾斜角度（以度為單位）。

## 範例
以下是一個簡單的範例，展示如何使用 `ondeviceorientation` 事件來獲取設備的方向資訊：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Device Orientation Example</title>
</head>
<body>
    <h1>設備方向資訊</h1>
    <div id="output"></div>
    
    <script>
        window.addEventListener("deviceorientation", function(event) {
            const output = document.getElementById("output");
            output.innerHTML = `
                Alpha: ${event.alpha}°<br>
                Beta: ${event.beta}°<br>
                Gamma: ${event.gamma}°
            `;
        });
    </script>
</body>
</html>
```

## 解釋
在使用 `ondeviceorientation` 時，有幾個常見的注意事項：
- **設備兼容性**：並非所有設備都支持 `ondeviceorientation`。建議在使用前檢查設備是否支持該功能。
- **隱私權要求**：某些瀏覽器可能要求用戶授權才能訪問設備的方向資訊，特別是在使用 HTTPS 的情況下。
- **事件頻率**：事件的觸發頻率可能會受到設備性能和其他因素的影響，開發者需考慮性能優化。

## 一句總結
`ondeviceorientation` 事件允許開發者捕捉設備的方向變化，從而提升用戶互動體驗。