<!--
Meta Description: # DeviceMotionEvent: 자바스크립트에서의 기기 운동 이벤트 ## 개요 DeviceMotionEvent는 웹에서 모바일 기기의 가속도 및 회전 정보를 실시간으로 제공하는 이벤트로, 사용자가 기기를 움직일 때 발생하는 물리적 데이터를 수집할 수 있게 해줍니다...
Meta Keywords: event, 기기의, console, log, acceleration
-->

# DeviceMotionEvent: 자바스크립트에서의 기기 운동 이벤트

## 개요
DeviceMotionEvent는 웹에서 모바일 기기의 가속도 및 회전 정보를 실시간으로 제공하는 이벤트로, 사용자가 기기를 움직일 때 발생하는 물리적 데이터를 수집할 수 있게 해줍니다.

## 문서
### 목적
DeviceMotionEvent는 기기의 움직임을 감지하고 이를 웹 애플리케이션에서 활용할 수 있도록 해줍니다. 이 이벤트는 주로 게임, 증강 현실(AR) 및 인터랙티브 애플리케이션에서 사용됩니다.

### 사용법
구현하기 위해서는 먼저 `DeviceMotionEvent`를 사용할 수 있는지 확인하고, `devicemotion` 이벤트 리스너를 추가해야 합니다.

```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        // event.acceleration: 기기의 가속도
        // event.rotationRate: 기기의 회전 속도
        console.log('X:', event.acceleration.x);
        console.log('Y:', event.acceleration.y);
        console.log('Z:', event.acceleration.z);
        console.log('Rotation Alpha:', event.rotationRate.alpha);
        console.log('Rotation Beta:', event.rotationRate.beta);
        console.log('Rotation Gamma:', event.rotationRate.gamma);
    });
} else {
    console.log('DeviceMotionEvent가 지원되지 않습니다.');
}
```

### 세부사항
- `event.acceleration`: 기기의 선형 가속도를 나타내는 객체로, X, Y, Z 축의 가속도를 포함합니다.
- `event.rotationRate`: 기기의 회전 속도를 나타내는 객체로, 알파, 베타, 감마 각도를 포함합니다.
- 사용자는 `DeviceMotionEvent`를 통해 기기의 움직임에 따라 UI를 변경하거나, 3D 그래픽을 조작하는 등의 작업을 수행할 수 있습니다.

## 예제
기기 움직임에 따라 색상을 변경하는 간단한 예제입니다.

```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        let x = event.acceleration.x;
        let y = event.acceleration.y;

        document.body.style.backgroundColor = `rgb(${Math.abs(x) * 10}, ${Math.abs(y) * 10}, 150)`;
    });
} else {
    console.log('DeviceMotionEvent가 지원되지 않습니다.');
}
```

## 설명
- **브라우저 호환성**: 모든 브라우저에서 지원되지 않으므로, 사용하기 전에 `DeviceMotionEvent`의 지원 여부를 확인해야 합니다.
- **보안 권한**: 최근 브라우저에서는 보안상의 이유로 기기 센서에 접근하기 위해 사용자로부터 권한을 요청해야 할 수 있습니다.
- **정확성 문제**: 기기의 센서 데이터는 외부 환경에 따라 다를 수 있으므로, 이를 고려하여 애플리케이션을 설계해야 합니다.

## 한 줄 요약
DeviceMotionEvent는 자바스크립트를 통해 모바일 기기의 가속도와 회전 정보를 실시간으로 제공하는 이벤트입니다.