<!--
Meta Description: # PresentationRequest: JavaScript에서의 화면 공유 요청 ## 개요 `PresentationRequest`는 웹 애플리케이션이 다른 디스플레이 장치에서 콘텐츠를 표시할 수 있도록 요청하는 JavaScript API입니다. 이를 통해 사용자는 T...
Meta Keywords: presentationrequest, 프레젠테이션, 디스플레이, 콘텐츠를, 애플리케이션이
-->

# PresentationRequest: JavaScript에서의 화면 공유 요청

## 개요
`PresentationRequest`는 웹 애플리케이션이 다른 디스플레이 장치에서 콘텐츠를 표시할 수 있도록 요청하는 JavaScript API입니다. 이를 통해 사용자는 TV, 프로젝터 등의 대형 화면에 콘텐츠를 송출할 수 있습니다.

## 문서화
### 목적
`PresentationRequest`는 웹 애플리케이션이 스마트 TV나 프로젝터와 같은 디스플레이 장치에 연결하여 콘텐츠를 전송할 수 있도록 지원합니다. 이 API는 웹 기반 프레젠테이션, 비디오 스트리밍 및 기타 멀티미디어 애플리케이션에 유용하게 사용됩니다.

### 사용법
`PresentationRequest`는 다음과 같은 메서드와 프로퍼티로 구성됩니다:

- **생성자**: `new PresentationRequest(urls)`
  - `urls`: 사용자가 전송할 수 있는 URI의 배열입니다.

- **메서드**:
  - `start()`: 프레젠테이션 세션을 시작합니다.
  - `getAvailability()`: 현재 사용 가능한 프레젠테이션 디스플레이 장치를 확인합니다.

- **이벤트**:
  - `onconnectionavailable`: 새로운 연결이 가능할 때 호출됩니다.
  - `onconnectionclosed`: 연결이 종료될 때 호출됩니다.

### 세부사항
`PresentationRequest`를 사용하기 위해서는 사용자의 허가가 필요합니다. 사용자가 연결을 승인하면, 애플리케이션은 해당 디스플레이 장치에 콘텐츠를 전송할 수 있습니다. 이 API는 비동기적으로 작동하므로, Promise를 사용하여 연결 상태를 관리하는 것이 일반적입니다.

## 예제
아래는 `PresentationRequest`의 기본 사용 예제입니다:

```javascript
// 프레젠테이션 요청 생성
const request = new PresentationRequest(['https://example.com/presentation']);

// 프레젠테이션 시작
request.start().then((connection) => {
    console.log('프레젠테이션 연결 성공:', connection);
}).catch((error) => {
    console.error('프레젠테이션 연결 실패:', error);
});
```

## 설명
`PresentationRequest`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **브라우저 지원**: 모든 브라우저에서 이 API를 지원하지 않을 수 있으므로, 사용 전에 지원 여부를 확인해야 합니다.
- **사용자 승인**: 사용자가 수동으로 연결을 승인해야 하므로, UI/UX를 고려하여 적절한 안내 메시지를 제공해야 합니다.
- **비동기 처리**: 연결 요청이 비동기적으로 처리되므로, Promise를 사용하여 연결 상태를 관리하는 것이 중요합니다.

## 한 줄 요약
`PresentationRequest`는 웹 애플리케이션이 외부 디스플레이 장치에 콘텐츠를 전송하기 위한 JavaScript API입니다.