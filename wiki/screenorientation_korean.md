<!--
Meta Description: # ScreenOrientation: 자바스크립트에서 화면 방향 제어하기 ## 개요 `ScreenOrientation` API는 웹 애플리케이션에서 화면 방향을 제어하고 모니터링하는 기능을 제공합니다. 이를 통해 사용자는 디바이스의 화면 회전 상태를 확인하고, 필요에 ...
Meta Keywords: orientation, screen, screenorientation, 방향을, 있습니다
-->

# ScreenOrientation: 자바스크립트에서 화면 방향 제어하기

## 개요
`ScreenOrientation` API는 웹 애플리케이션에서 화면 방향을 제어하고 모니터링하는 기능을 제공합니다. 이를 통해 사용자는 디바이스의 화면 회전 상태를 확인하고, 필요에 따라 명시적으로 방향을 설정할 수 있습니다.

## 문서화
### 목적
`ScreenOrientation` API는 모바일 및 태블릿 디바이스에서의 사용자 경험을 향상시키기 위해 설계되었습니다. 이 API를 사용하면 애플리케이션이 특정 방향으로 전환되도록 강제할 수 있으며, 화면 방향 변경에 대한 이벤트를 수신할 수 있습니다.

### 사용법
`ScreenOrientation` API는 `screen.orientation` 객체를 통해 접근할 수 있습니다. 주요 속성과 메서드는 다음과 같습니다:

- **속성**
  - `type`: 현재 화면 방향의 타입을 반환합니다. 예: `"portrait-primary"`, `"landscape-secondary"` 등.
  - `angle`: 현재 화면의 회전 각도를 반환합니다.

- **메서드**
  - `lock(orientation)`: 지정된 방향으로 화면을 고정합니다.
  - `unlock()`: 화면 방향 고정을 해제합니다.
  - `addEventListener(type, listener)`: 화면 방향 변경 이벤트를 수신하기 위한 리스너를 추가합니다.
  - `removeEventListener(type, listener)`: 리스너를 제거합니다.

### 예제
```javascript
// 화면 방향 정보 가져오기
if (screen.orientation) {
    console.log(`현재 방향: ${screen.orientation.type}`);
    console.log(`회전 각도: ${screen.orientation.angle}`);
}

// 화면 방향 고정하기
function lockOrientation() {
    screen.orientation.lock('portrait').then(() => {
        console.log('화면 방향이 세로로 고정되었습니다.');
    }).catch((error) => {
        console.error(`방향 고정 실패: ${error}`);
    });
}

// 방향 변경 이벤트 리스너 추가하기
screen.orientation.addEventListener('change', () => {
    console.log(`새로운 방향: ${screen.orientation.type}`);
});
```

### 설명
- **일반적인 함정**
  - `ScreenOrientation` API는 모든 브라우저에서 지원되지 않을 수 있습니다. 따라서 지원 여부를 확인하는 것이 중요합니다.
  - 화면 방향을 고정하려고 시도할 때, 사용자의 권한이나 브라우저 설정에 따라 실패할 수 있습니다.

- **주의 사항**
  - 화면 방향이 변경되면 사용자 경험에 영향을 줄 수 있으므로, 방향을 강제로 고정하는 것은 신중해야 합니다.
  - 모바일 디바이스의 경우, 사용자가 화면 방향을 변경하는 것을 막는 것은 사용자의 불편을 초래할 수 있습니다.

## 한 줄 요약
`ScreenOrientation` API는 자바스크립트를 통해 웹 애플리케이션의 화면 방향을 제어하고 모니터링할 수 있는 기능을 제공합니다.