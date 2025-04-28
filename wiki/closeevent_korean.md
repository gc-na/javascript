<!--
Meta Description: # JavaScript CloseEvent: 웹 소켓 연결 종료 이벤트 ## 개요 CloseEvent는 JavaScript의 웹 소켓 API에서 소켓 연결이 종료될 때 발생하는 이벤트로, 연결이 닫혔을 때의 상태 정보를 제공합니다. 이 이벤트는 클라이언트와 서버 간의 ...
Meta Keywords: 연결이, event, console, log, closeevent는
-->

# JavaScript CloseEvent: 웹 소켓 연결 종료 이벤트

## 개요
CloseEvent는 JavaScript의 웹 소켓 API에서 소켓 연결이 종료될 때 발생하는 이벤트로, 연결이 닫혔을 때의 상태 정보를 제공합니다. 이 이벤트는 클라이언트와 서버 간의 통신에서 중요한 역할을 합니다.

## 문서화
CloseEvent는 웹 소켓 연결이 정상적으로 종료되었거나 오류로 인해 종료될 때 발생합니다. 이 이벤트는 주로 `onclose` 이벤트 핸들러에서 다루어지며, 연결이 종료될 때의 상태 코드와 이유를 확인할 수 있습니다.

### 목적
- 웹 소켓 연결 상태를 확인하고, 연결이 종료되었을 때 적절한 조치를 취할 수 있도록 합니다.

### 사용법
CloseEvent는 다음과 같은 속성을 가집니다:
- `code`: 연결 종료의 상태 코드를 나타내는 숫자입니다.
- `reason`: 연결이 종료된 이유를 설명하는 문자열입니다.
- `wasClean`: 연결이 정상적으로 종료되었는지를 나타내는 불리언 값입니다.

### 기본 사용법
CloseEvent를 사용하기 위해서는 웹 소켓 객체를 생성하고, `onclose` 이벤트 리스너를 추가합니다.

```javascript
const socket = new WebSocket('wss://example.com/socket');

socket.onopen = function(event) {
    console.log('연결이 열렸습니다.');
};

socket.onclose = function(event) {
    console.log('연결이 닫혔습니다.');
    console.log('상태 코드:', event.code);
    console.log('이유:', event.reason);
    console.log('정상 종료:', event.wasClean);
};
```

## 설명
CloseEvent를 사용할 때 주의해야 할 점은 다음과 같습니다:
- 연결이 닫히는 이유는 여러 가지가 있을 수 있으며, 이는 서버의 상태나 네트워크 문제 등에 따라 달라집니다.
- `code` 속성은 RFC 6455에 정의된 표준 상태 코드를 따릅니다. 예를 들어, 1000은 정상 종료를 의미합니다.
- `reason` 속성은 선택적이며, 서버 측에서 제공하지 않는 경우 기본값이 없습니다.
- `wasClean` 속성은 연결이 정상적으로 종료되었는지를 알려주며, 이 값이 `false`일 경우 추가적인 오류 처리가 필요할 수 있습니다.

## 한 줄 요약
CloseEvent는 웹 소켓 연결 종료 시 발생하는 이벤트로, 연결 상태 코드 및 종료 이유를 제공합니다.