<!--
Meta Description: # XRReferenceSpace: JavaScript에서 XR 경험을 위한 기초 ## 개요 `XRReferenceSpace`는 WebXR API의 중요한 구성 요소로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 객체의 위치와 방향을 정의하는 데 사용됩니다. 이 ...
Meta Keywords: local, session, xrreferencespace, then, function
-->

# XRReferenceSpace: JavaScript에서 XR 경험을 위한 기초

## 개요
`XRReferenceSpace`는 WebXR API의 중요한 구성 요소로, 가상 현실(VR) 및 증강 현실(AR) 환경에서 객체의 위치와 방향을 정의하는 데 사용됩니다. 이 객체는 사용자와 XR 장치 간의 관계를 이해하고, XR 콘텐츠의 위치를 정확하게 설정하는 데 도움을 줍니다.

## 문서화
`XRReferenceSpace`는 XR 세션에서 사용되는 좌표계로, 사용자의 현재 위치와 방향을 기준으로 공간을 정의합니다. 이를 통해 개발자는 가상 객체를 현실 세계에 올바르게 배치할 수 있습니다.

### 목적
- XR 환경에서의 위치 및 방향 관리를 단순화합니다.
- 다양한 좌표계 (예: Local, Local Floor, Unbounded) 지원을 통해 유연성을 제공합니다.

### 사용법
`XRReferenceSpace`는 WebXR 세션에서 생성되며, 다음과 같은 방법으로 사용됩니다:

1. **XR 세션 시작**: `navigator.xr.requestSession()` 메서드를 사용하여 XR 세션을 시작합니다.
2. **참조 공간 생성**: 세션 객체의 `requestReferenceSpace()` 메서드를 호출하여 원하는 참조 공간 유형을 요청합니다.

#### 예시 코드
```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
    return session.requestReferenceSpace('local');
}).then(function(referenceSpace) {
    console.log('Reference Space:', referenceSpace);
});
```

## 예제
### 기본 사용 예
```javascript
navigator.xr.requestSession('immersive-vr').then(function(session) {
    return session.requestReferenceSpace('local-floor');
}).then(function(referenceSpace) {
    console.log('Local Floor Reference Space:', referenceSpace);
});
```

### 여러 참조 공간 예
```javascript
navigator.xr.requestSession('immersive-ar').then(function(session) {
    return Promise.all([
        session.requestReferenceSpace('local'),
        session.requestReferenceSpace('unbounded')
    ]);
}).then(function(referenceSpaces) {
    console.log('Local Reference Space:', referenceSpaces[0]);
    console.log('Unbounded Reference Space:', referenceSpaces[1]);
});
```

## 설명
`XRReferenceSpace`를 사용할 때 주의할 점은 다음과 같습니다:

- **좌표계의 선택**: 각 참조 공간 유형은 서로 다른 목적을 가지고 있으며, 상황에 맞는 적절한 유형을 선택하는 것이 중요합니다.
- **지원되는 장치**: 모든 VR 및 AR 장치가 동일한 참조 공간을 지원하지 않으므로, 디바이스의 문서를 확인해야 합니다.
- **세션 상태**: XR 세션이 활성 상태일 때만 참조 공간을 요청할 수 있습니다.

## 한 줄 요약
`XRReferenceSpace`는 WebXR API에서 XR 환경의 위치 및 방향을 정의하는 데 필수적인 객체입니다.