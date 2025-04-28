<!--
Meta Description: # XRInputSourcesChangeEvent: 자바스크립트에서 XR 입력 소스 변경 이벤트에 대한 이해 ## 개요 XRInputSourcesChangeEvent는 WebXR API의 이벤트 중 하나로, XR(확장 현실) 환경에서 입력 소스(예: 컨트롤러, 핸드트래...
Meta Keywords: inputsource, event, xrinputsourceschangeevent는, session, webxr
-->

# XRInputSourcesChangeEvent: 자바스크립트에서 XR 입력 소스 변경 이벤트에 대한 이해

## 개요
XRInputSourcesChangeEvent는 WebXR API의 이벤트 중 하나로, XR(확장 현실) 환경에서 입력 소스(예: 컨트롤러, 핸드트래킹) 변경 사항을 감지하는 데 사용됩니다. 이 이벤트는 입력 소스가 추가되거나 제거될 때 발생하여 개발자가 XR 경험을 동적으로 조정할 수 있도록 돕습니다.

## 문서화
XRInputSourcesChangeEvent는 WebXR 세션에서 입력 소스의 상태가 변경될 때 발생하는 이벤트입니다. 이 이벤트는 `XRSession` 객체에 의해 발생하며, 입력 소스의 목록을 업데이트하고 사용자와의 상호작용을 관리하는 데 중요한 역할을 합니다.

### 목적
XRInputSourcesChangeEvent는 개발자가 사용자의 입력 장치 변경을 감지하고, 이를 기반으로 사용자 인터페이스나 상호작용을 동적으로 업데이트할 수 있도록 지원합니다.

### 사용법
XRInputSourcesChangeEvent는 다음과 같은 방식으로 사용할 수 있습니다:

1. XRSession을 시작합니다.
2. `select` 이벤트를 수신하여 입력 소스 변경 사항을 감지합니다.
3. 변경된 입력 소스에 대한 처리를 구현합니다.

```javascript
let session = null;

navigator.xr.requestSession('immersive-vr').then((xrSession) => {
    session = xrSession;

    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log('입력 소스 추가:', inputSource);
        });
        event.removed.forEach((inputSource) => {
            console.log('입력 소스 제거:', inputSource);
        });
    });
});
```

## 예제
아래는 XRInputSourcesChangeEvent를 활용한 기본적인 예제입니다.

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceschange', (event) => {
        // 추가된 입력 소스 출력
        event.added.forEach((inputSource) => {
            console.log('추가된 입력 소스:', inputSource);
        });

        // 제거된 입력 소스 출력
        event.removed.forEach((inputSource) => {
            console.log('제거된 입력 소스:', inputSource);
        });
    });
});
```

## 설명
XRInputSourcesChangeEvent를 사용할 때 주의할 점은 다음과 같습니다:

- **이벤트 발생 타이밍**: 입력 소스가 추가되거나 제거되는 즉시 이벤트가 발생하므로, 이벤트 핸들러에서 상태를 즉시 업데이트해야 합니다.
- **여러 입력 소스**: XR 환경에서는 여러 입력 소스가 동시에 존재할 수 있으므로, 각 입력 소스에 대한 개별 처리가 필요합니다.
- **브라우저 지원**: WebXR API는 모든 브라우저에서 동일하게 지원되지 않으므로, 사용 전 브라우저 호환성을 확인해야 합니다.
- **상태 관리**: 입력 소스의 추가 및 제거에 따라 UI 또는 게임 상태를 적절히 관리하는 것이 중요합니다.

## 한 줄 요약
XRInputSourcesChangeEvent는 WebXR 환경에서 입력 소스의 변경을 감지하여 사용자 인터페이스를 동적으로 조정할 수 있도록 돕는 이벤트입니다.