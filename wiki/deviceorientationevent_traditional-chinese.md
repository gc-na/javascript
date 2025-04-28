<!--
Meta Description: # DeviceOrientationEvent：JavaScript 中的設備方向事件 ## 概述 `DeviceOrientationEvent` 是一個用於獲取設備方向的事件，允許開發者訪問設備在三維空間中的方位。這對於開發增強現實 (AR)、虛擬現實 (VR) 和其他基於運動的應用程序至關重...
Meta Keywords: deviceorientationevent, alpha, beta, gamma, event
-->

# DeviceOrientationEvent：JavaScript 中的設備方向事件

## 概述
`DeviceOrientationEvent` 是一個用於獲取設備方向的事件，允許開發者訪問設備在三維空間中的方位。這對於開發增強現實 (AR)、虛擬現實 (VR) 和其他基於運動的應用程序至關重要。

## 文件說明
`DeviceOrientationEvent` 事件描述了設備的方向，通常是手機或平板電腦。它提供了設備相對於世界坐標系的 alpha、beta 和 gamma 值，分別代表圍繞 Z 軸、X 軸和 Y 軸的旋轉。

### 目的
`DeviceOrientationEvent` 的主要用途是讓開發者獲取設備的方向數據，從而實現基於方向的互動功能。

### 使用方法
要使用 `DeviceOrientationEvent`，需要添加事件監聽器來接收方向數據。以下是基本的使用方法：

```javascript
window.addEventListener('deviceorientation', function(event) {
    const alpha = event.alpha; // 繞 Z 軸的旋轉
    const beta = event.beta;   // 繞 X 軸的旋轉
    const gamma = event.gamma; // 繞 Y 軸的旋轉

    console.log(`Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
});
```

### 事件屬性
- **alpha**：設備繞 Z 軸的旋轉角度（0 到 360 度）。
- **beta**：設備繞 X 軸的旋轉角度（-180 到 180 度）。
- **gamma**：設備繞 Y 軸的旋轉角度（-90 到 90 度）。

## 範例
以下是一個簡單的範例，顯示如何使用 `DeviceOrientationEvent` 來改變網頁上的元素方向：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>DeviceOrientationEvent 範例</title>
    <style>
        #box {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
        }
    </style>
</head>
<body>
    <div id="box"></div>
    <script>
        const box = document.getElementById('box');

        window.addEventListener('deviceorientation', function(event) {
            const alpha = event.alpha;
            box.style.transform = `rotateY(${alpha}deg)`;
        });
    </script>
</body>
</html>
```

## 解釋
在使用 `DeviceOrientationEvent` 時，有幾個常見的陷阱和注意事項：
- **隱私權問題**：從 iOS 13 開始，使用 `DeviceOrientationEvent` 需要用戶的明確許可。開發者需確保在調用此事件時，提示用戶授予權限。
- **不支持的設備**：並非所有設備都支持設備方向事件。開發者應檢查用戶的設備是否支持這項功能。
- **事件頻率**：`deviceorientation` 事件的觸發頻率可能會因設備而異，因此應考慮性能優化。

## 一句話總結
`DeviceOrientationEvent` 是一個用於獲取設備方向數據的事件，對於開發基於運動的應用程序至關重要。