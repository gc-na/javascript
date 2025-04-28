<!--
Meta Description: # XRInputSource: 자바스크립트에서의 XR 입력 소스 ## 개요 XRInputSource는 웹XR API의 일부로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 사용자 입력 장치에 대한 정보를 제공합니다. 이 객체는 사용자가 VR 또는 AR 경험에서 상호...
Meta Keywords: xrinputsource는, 정보를, 장치의, inputsource, event
-->

# XRInputSource: 자바스크립트에서의 XR 입력 소스

## 개요
XRInputSource는 웹XR API의 일부로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 사용자 입력 장치에 대한 정보를 제공합니다. 이 객체는 사용자가 VR 또는 AR 경험에서 상호작용할 때 발생하는 입력을 처리하는 데 필수적입니다.

## 문서
### 목적
XRInputSource는 사용자의 입력 장치(예: VR 컨트롤러, 터치 스크린 등)에 대한 정보를 제공하여, 개발자가 이러한 장치를 통해 사용자와 상호작용할 수 있도록 도와줍니다. 이를 통해 더욱 몰입감 있는 환경을 구축할 수 있습니다.

### 사용법
XRInputSource는 XRSession의 `inputSources` 배열에서 사용할 수 있습니다. 각 XRInputSource 객체는 해당 입력 장치의 상태, 위치, 및 제공하는 입력 유형에 대한 정보를 포함합니다.

#### 주요 속성
- **handedness**: 입력 장치의 손잡이 정보(왼손, 오른손)를 나타냅니다.
- **pointerOrigin**: 입력 장치의 위치를 3D 공간에서 정의합니다.
- **targetRaySpace**: 입력 장치가 가리키는 방향을 나타내는 공간입니다.
- **gamepad**: 입력 장치가 게임패드일 경우, 해당 게임패드의 정보를 포함합니다.

### 사용 예시
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('selectstart', event => {
        const inputSource = event.inputSource;
        console.log('Input source handedness:', inputSource.handedness);
    });

    session.addEventListener('inputsourceschange', event => {
        event.added.forEach(inputSource => {
            console.log('New input source detected:', inputSource);
        });
    });
});
```

## 설명
XRInputSource를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **호환성**: XRInputSource는 모든 브라우저에서 지원되지 않으므로, 사용하고자 하는 기능이 호환되는지 확인해야 합니다.
- **상태 업데이트**: 입력 장치의 상태는 주기적으로 업데이트됩니다. 따라서 상태 변경 이벤트를 등록하여 적절히 처리하는 것이 중요합니다.
- **다양한 입력 장치**: 여러 종류의 입력 장치가 존재하며, 각 장치의 특성을 이해하고 적절히 처리해야 합니다. 예를 들어, 게임패드와 VR 컨트롤러는 다른 방식으로 입력을 처리합니다.

## 한 줄 요약
XRInputSource는 웹XR API에서 사용자의 입력 장치 정보를 제공하여 VR 및 AR 환경에서의 상호작용을 지원하는 객체입니다.