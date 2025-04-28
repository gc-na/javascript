<!--
Meta Description: # DevicePosture: 자바스크립트에서의 기기 자세 감지 ## 개요 DevicePosture는 자바스크립트를 사용하여 사용자의 기기 자세(가로, 세로, 태블릿 또는 휴대폰)를 감지하고 이에 따라 웹 애플리케이션의 UI를 동적으로 조정할 수 있는 기능입니다. 이 ...
Meta Keywords: deviceposture는, 사용자의, 자세를, window, matchmedia
-->

# DevicePosture: 자바스크립트에서의 기기 자세 감지

## 개요
DevicePosture는 자바스크립트를 사용하여 사용자의 기기 자세(가로, 세로, 태블릿 또는 휴대폰)를 감지하고 이에 따라 웹 애플리케이션의 UI를 동적으로 조정할 수 있는 기능입니다. 이 기능은 다양한 장치에서의 사용자 경험을 최적화하는 데 유용합니다.

## 문서
### 목적
DevicePosture는 웹 애플리케이션이 사용자의 기기 자세를 감지하여 적절한 레이아웃과 스타일을 적용할 수 있도록 합니다. 이를 통해 모바일 및 데스크톱 장치에서 사용자 경험을 향상시킬 수 있습니다.

### 사용법
DevicePosture는 일반적으로 `window.matchMedia()` 메서드를 사용하여 미디어 쿼리를 통해 기기 자세를 감지합니다. 다음은 기기 자세를 감지하는 기본적인 방법입니다:

```javascript
const devicePosture = window.matchMedia("(orientation: portrait)");

if (devicePosture.matches) {
    console.log("기기가 세로 방향입니다.");
} else {
    console.log("기기가 가로 방향입니다.");
}
```

이 코드에서는 사용자의 기기가 세로 방향인지 가로 방향인지 판단하고, 그에 따라 콘솔에 메시지를 출력합니다.

## 예제
### 세로 및 가로 방향 감지

```javascript
function checkDevicePosture() {
    const orientation = window.matchMedia("(orientation: portrait)");

    if (orientation.matches) {
        document.body.classList.add("portrait");
        document.body.classList.remove("landscape");
    } else {
        document.body.classList.add("landscape");
        document.body.classList.remove("portrait");
    }
}

window.addEventListener("resize", checkDevicePosture);
checkDevicePosture(); // 초기 체크
```

이 예제는 사용자가 기기의 방향을 변경할 때마다 DOM에 클래스를 추가하거나 제거하여 스타일을 변경합니다.

## 설명
### 일반적인 함정 및 주의사항
- **이벤트 리스너**: 기기의 방향이 변경될 때마다 이벤트를 리스닝해야 하므로, `resize` 이벤트를 적절히 관리해야 합니다.
- **브라우저 호환성**: 모든 브라우저가 `matchMedia`를 지원하지 않을 수 있으므로, 호환성을 고려하여 대체 방법을 마련하는 것이 좋습니다.
- **성능 문제**: `resize` 이벤트는 빈번하게 발생할 수 있으므로, 성능 최적화를 위해 쓰로틀링 또는 디바운싱 기법을 사용하는 것이 좋습니다.

## 한줄 요약
DevicePosture는 자바스크립트를 통해 사용자의 기기 자세를 감지하고, 이에 따라 웹 애플리케이션의 UI를 조정할 수 있는 기능입니다.