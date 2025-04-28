<!--
Meta Description: # XRInputSourceArray: 자바스크립트에서의 XR 입력 소스 배열 ## 개요 `XRInputSourceArray`는 WebXR API의 일부로, 가상현실(VR) 및 증강현실(AR) 환경에서 사용자의 입력 장치를 나타내는 배열입니다. 이 배열은 XR 세션 동...
Meta Keywords: xrinputsourcearray, 소스의, inputsource, 정보를, xrsession
-->

# XRInputSourceArray: 자바스크립트에서의 XR 입력 소스 배열

## 개요
`XRInputSourceArray`는 WebXR API의 일부로, 가상현실(VR) 및 증강현실(AR) 환경에서 사용자의 입력 장치를 나타내는 배열입니다. 이 배열은 XR 세션 동안 사용자의 컨트롤러, 트래킹 포인트 및 입력 장치에 대한 정보를 제공합니다.

## 문서화

### 목적
`XRInputSourceArray`는 사용자가 XR 환경에서 상호작용할 수 있는 입력 소스의 리스트를 제공합니다. 이 배열은 각 입력 소스의 상태와 정보를 포함하고 있어, 개발자가 다양한 입력 장치와 상호작용하는 애플리케이션을 개발하는 데 유용합니다.

### 사용법
`XRInputSourceArray`는 `XRSession` 객체의 `inputSources` 프로퍼티를 통해 접근할 수 있습니다. 이 프로퍼티는 현재 세션에서 사용 가능한 모든 입력 소스의 배열을 반환합니다.

```javascript
let xrSession = await navigator.xr.requestSession('immersive-vr');
xrSession.addEventListener('selectstart', (event) => {
    const inputSources = xrSession.inputSources;
    inputSources.forEach(inputSource => {
        console.log(inputSource);
    });
});
```

### 세부 사항
- **구조**: `XRInputSource` 객체는 각 입력 소스에 대한 정보를 포함합니다. 이 객체는 다음과 같은 프로퍼티를 가집니다:
  - `handedness`: 입력 소스의 손에 대한 정보 (왼손, 오른손 등).
  - `targetRayMode`: 입력 소스의 레이 모드 (예: `tracked-pointer`, `gaze`).
  - `gripSpace`: 입력 소스에 대한 그립 공간.
  - `gamepad`: 게임패드와 같은 입력 소스일 경우, 추가적인 정보를 제공합니다.

## 예제
아래는 XRInputSourceArray를 사용하는 간단한 예제입니다.

```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach(inputSource => {
            console.log('추가된 입력 소스:', inputSource);
        });
        event.removed.forEach(inputSource => {
            console.log('제거된 입력 소스:', inputSource);
        });
    });
});
```

## 설명
`XRInputSourceArray`를 사용할 때 주의해야 할 점은 다음과 같습니다:
- 입력 소스는 XR 세션이 활성화되고 사용자가 장치를 연결할 때만 사용할 수 있습니다.
- 입력 소스의 상태는 세션의 상태에 따라 다를 수 있으므로, 항상 최신 상태를 확인해야 합니다.
- 일부 장치는 특정 브라우저에서만 지원될 수 있으므로, 호환성에 주의해야 합니다.

## 한 줄 요약
`XRInputSourceArray`는 WebXR API에서 사용자의 입력 장치를 나타내는 배열로, XR 환경에서의 상호작용을 용이하게 합니다.