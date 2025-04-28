<!--
Meta Description: # MediaKeyStatusMap: JavaScript에서의 미디어 키 상태 관리 ## 개요 `MediaKeyStatusMap`는 JavaScript의 Encrypted Media Extensions (EME) API의 일부로, 미디어 콘텐츠의 DRM(디지털 저작권 ...
Meta Keywords: 상태를, mediakeystatusmap, 미디어, drm, mediakeysession
-->

# MediaKeyStatusMap: JavaScript에서의 미디어 키 상태 관리

## 개요
`MediaKeyStatusMap`는 JavaScript의 Encrypted Media Extensions (EME) API의 일부로, 미디어 콘텐츠의 DRM(디지털 저작권 관리) 상태를 관리하기 위한 기능입니다. 이 객체는 미디어 키의 상태를 추적하고, 각 키의 현재 상태에 대한 정보를 제공합니다.

## 문서화
`MediaKeyStatusMap`는 여러 미디어 키의 상태를 나타내는 맵 객체입니다. 이 객체는 비디오 또는 오디오 스트림과 같은 멀티미디어 콘텐츠를 재생할 때, DRM 키의 상태를 확인하고 관리하는 데 사용됩니다.

### 목적
`MediaKeyStatusMap`는 개발자가 미디어 키의 상태를 쉽게 확인하고 제어할 수 있게 해줍니다. 이를 통해 DRM 보호 콘텐츠의 재생 관리 및 오류 처리를 용이하게 합니다.

### 사용법
`MediaKeyStatusMap`는 `MediaKeys` 인터페이스와 함께 사용되며, 다음과 같이 동작합니다:

1. DRM 보호 미디어 콘텐츠를 로드합니다.
2. `MediaKeySystemAccess` 객체를 통해 미디어 키 시스템을 요청합니다.
3. `MediaKeySession` 객체를 생성하여 미디어 키 세션을 시작합니다.
4. `MediaKeyStatusMap`를 사용하여 키의 상태를 확인합니다.

### 세부 사항
- `MediaKeyStatusMap`는 키 식별자와 키 상태의 쌍으로 구성됩니다.
- 키 상태는 `usable`, `expired`, `output-restricted`, `internal-error` 등의 상태를 가질 수 있습니다.
- 이 객체는 `get()` 메서드를 통해 특정 키의 상태를 조회할 수 있습니다.

## 예제
```javascript
// MediaKeySystemAccess 요청
navigator.requestMediaKeySystemAccess('com.example.drm', [{
  initDataTypes: ['cenc'],
  audioCapabilities: [{ contentType: 'audio/mp4; codecs="mp4a.40.2"' }],
}]).then(function(keySystemAccess) {
  return keySystemAccess.createMediaKeys();
}).then(function(mediaKeys) {
  // MediaKeySession 생성
  var mediaKeySession = mediaKeys.createSession();
  return mediaKeySession.generateRequest('cenc', initData);
}).then(function() {
  // MediaKeyStatusMap 사용
  var statusMap = mediaKeySession.keyStatuses;
  statusMap.forEach((status, keyId) => {
    console.log(`Key ID: ${keyId}, Status: ${status}`);
  });
}).catch(function(error) {
  console.error('Error:', error);
});
```

## 설명
`MediaKeyStatusMap`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- 키 상태는 비동기적으로 업데이트되므로, 상태를 확인하기 전에 반드시 키 세션이 활성화되어 있어야 합니다.
- `MediaKeyStatusMap`에 포함된 키 식별자는 고유해야 하며, 각 키의 상태는 DRM 정책에 따라 다를 수 있습니다.
- 상태를 변경할 수 있는 방법은 없으며, 오직 상태를 조회하는 용도로만 사용됩니다.

## 한 줄 요약
`MediaKeyStatusMap`는 JavaScript에서 DRM 키의 상태를 관리하고 확인하는 데 사용되는 객체입니다.