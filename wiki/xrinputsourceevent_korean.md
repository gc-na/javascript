<!--
Meta Description: # XRInputSourceEvent: JavaScript에서 XR 입력 소스 이벤트 처리하기 ## 개요 XRInputSourceEvent는 WebXR API의 일부로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 입력 소스를 나타내는 이벤트입니다. 이 이벤트는 사...
Meta Keywords: event, function, session, addeventlistener, console
-->

# XRInputSourceEvent: JavaScript에서 XR 입력 소스 이벤트 처리하기

## 개요
XRInputSourceEvent는 WebXR API의 일부로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 입력 소스를 나타내는 이벤트입니다. 이 이벤트는 사용자의 인터랙션을 기반으로 다양한 입력 장치(예: 컨트롤러, 핸드트래킹 등)의 상태를 추적하고 처리하는 데 사용됩니다.

## 문서
XRInputSourceEvent는 사용자가 XR 환경 내에서 입력 장치를 사용할 때 발생하는 이벤트입니다. 이 이벤트는 XRSession의 `selectstart`, `selectend`, `squeezestart`, `squeezeend` 이벤트와 연결되어 있으며, 각 입력 장치의 상태 변경을 감지하고 처리하는 데 중요한 역할을 합니다.

### 목적
이벤트의 주요 목적은 사용자가 XR 환경에서 입력 장치를 통해 상호작용할 수 있도록 하여, 보다 몰입감 있는 경험을 제공하는 것입니다.

### 사용법
XRInputSourceEvent는 이벤트 리스너를 통해 처리됩니다. 이를 위해 WebXR API의 `addEventListener` 메서드를 사용하여 이벤트를 구독할 수 있습니다.

```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
    session.addEventListener('selectstart', function(event) {
        console.log('Selection started:', event);
    });

    session.addEventListener('selectend', function(event) {
        console.log('Selection ended:', event);
    });
});
```

## 예시
### 기본 사용 예제
다음은 XRInputSourceEvent를 사용하여 VR 세션에서 선택 이벤트를 처리하는 간단한 예입니다.

```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
    session.addEventListener('selectstart', function(event) {
        const inputSource = event.inputSource;
        console.log('Input source selected:', inputSource);
    });

    session.addEventListener('selectend', function(event) {
        console.log('Input source deselected:', event.inputSource);
    });
});
```

### 핸드 트래킹 예제
핸드 트래킹을 사용하는 XRInputSourceEvent의 예입니다.

```javascript
navigator.xr.requestSession('immersive-ar').then(function(session) {
    session.addEventListener('squeezestart', function(event) {
        console.log('Hand squeezed:', event.inputSource);
    });

    session.addEventListener('squeezeend', function(event) {
        console.log('Hand released:', event.inputSource);
    });
});
```

## 설명
XRInputSourceEvent를 사용할 때 주의해야 할 사항은 다음과 같습니다.

- **이벤트 리스너 등록:** 적절한 세션에 이벤트 리스너를 등록하는 것이 중요합니다. 세션이 활성화되지 않으면 이벤트가 발생하지 않습니다.
- **다양한 입력 소스:** XRInputSourceEvent는 여러 종류의 입력 장치에 대해 발생할 수 있습니다. 이를 처리하기 위해서는 입력 소스의 유형을 확인해야 할 필요가 있습니다.
- **성능 최적화:** 이벤트 리스너에서의 복잡한 로직은 성능 저하를 초래할 수 있으므로, 최적화가 필요합니다.

## 한 줄 요약
XRInputSourceEvent는 JavaScript에서 XR 환경의 입력 장치를 기반으로 이벤트를 처리하는 중요한 요소입니다.