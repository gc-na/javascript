<!--
Meta Description: # PresentationConnectionAvailableEvent: 자바스크립트에서의 활용 ## 개요 `PresentationConnectionAvailableEvent`는 웹 프레젠테이션 API의 일부로, 프레젠테이션 연결의 생성 가능성을 나타내는 이벤트입니다. ...
Meta Keywords: 프레젠테이션, presentationconnectionavailableevent, 새로운, 연결이, presentation
-->

# PresentationConnectionAvailableEvent: 자바스크립트에서의 활용

## 개요
`PresentationConnectionAvailableEvent`는 웹 프레젠테이션 API의 일부로, 프레젠테이션 연결의 생성 가능성을 나타내는 이벤트입니다. 이 이벤트는 새로운 프레젠테이션 연결이 생성될 때 발생하며, 웹 애플리케이션이 외부 디스플레이와 통신할 수 있도록 지원합니다.

## 문서
### 목적
`PresentationConnectionAvailableEvent`는 사용자가 새로운 프레젠테이션 연결을 만들 수 있을 때, 이를 알리기 위해 사용됩니다. 이 이벤트를 통해 개발자는 사용자에게 프레젠테이션 연결을 시작하라는 신호를 보낼 수 있습니다.

### 사용법
`PresentationConnectionAvailableEvent`는 `Presentation` 인터페이스의 `onconnectionavailable` 이벤트 핸들러를 통해 리스닝할 수 있습니다. 이 이벤트는 새로운 연결이 사용 가능해질 때마다 발생합니다.

### 세부 사항
- **이벤트 타입**: `PresentationConnectionAvailableEvent`
- **발생 시점**: 새로운 프레젠테이션 연결이 가능해질 때.
- **속성**:
  - `connection`: 새로 생성된 프레젠테이션 연결 객체입니다.

## 예제
아래는 `PresentationConnectionAvailableEvent`를 사용하는 기본적인 예제입니다.

```javascript
// 프레젠테이션 API 초기화
const presentation = new Presentation();

// 연결 가능 이벤트 리스너 추가
presentation.onconnectionavailable = (event) => {
    console.log("새로운 프레젠테이션 연결이 가능합니다.");
    const newConnection = event.connection;
    // 연결을 사용하여 추가 작업 수행
};

// 프레젠테이션 연결 요청
presentation.requestConnection();
```

## 설명
- **공통적인 실수**: 이벤트 리스너를 설정하기 전에 `requestConnection` 메서드를 호출하면 이벤트가 발생하지 않을 수 있습니다. 항상 이벤트 리스너를 먼저 설정한 후 연결 요청을 해야 합니다.
- **브라우저 호환성**: 일부 브라우저에서는 프레젠테이션 API를 지원하지 않을 수 있습니다. 따라서 기능을 사용하기 전에 브라우저 호환성을 확인해야 합니다.
- **추가 주의사항**: 이벤트가 발생하는 것은 새로운 연결이 가능하다는 것을 알리는 것이며, 사용자 인터페이스(UI)에서 적절한 피드백을 제공하는 것이 중요합니다.

## 한 문장 요약
`PresentationConnectionAvailableEvent`는 새로운 프레젠테이션 연결이 가능해질 때 발생하는 이벤트로, 웹 애플리케이션이 외부 디스플레이와 상호작용할 수 있도록 돕습니다.