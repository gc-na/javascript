<!--
Meta Description: # JavaScript EventSource: 실시간 서버 전송을 위한 API ## 개요 `EventSource`는 JavaScript에서 서버와의 실시간 양방향 통신을 가능하게 하는 API로, 웹 애플리케이션에서 지속적인 데이터를 수신할 수 있도록 지원합니다. 이 기...
Meta Keywords: eventsource, event, 실시간, 이벤트, 연결이
-->

# JavaScript EventSource: 실시간 서버 전송을 위한 API

## 개요
`EventSource`는 JavaScript에서 서버와의 실시간 양방향 통신을 가능하게 하는 API로, 웹 애플리케이션에서 지속적인 데이터를 수신할 수 있도록 지원합니다. 이 기술은 주로 서버 전송 이벤트(SSE)를 통해 사용되며, 클라이언트가 서버로부터 실시간 업데이트를 수신하는 데 유용합니다.

## 문서
`EventSource` 객체는 서버와 지속적인 연결을 생성하고, 서버에서 보낸 메시지를 자동으로 수신하는 기능을 제공합니다. 이 객체의 주요 목적은 웹 애플리케이션이 사용자에게 실시간 정보를 제공할 수 있도록 하는 것입니다.

### 사용법
`EventSource` 객체를 생성하려면 다음과 같은 구문을 사용합니다:

```javascript
const eventSource = new EventSource(url);
```

- **url**: 서버에서 이벤트 스트림을 제공하는 URL입니다.

### 주요 메서드 및 속성
- `onopen`: 연결이 성공적으로 열리면 호출되는 이벤트 핸들러입니다.
- `onmessage`: 서버에서 메시지를 수신할 때 호출되는 이벤트 핸들러입니다.
- `onerror`: 오류가 발생할 경우 호출되는 이벤트 핸들러입니다. 연결이 닫히거나 재연결을 시도할 때도 호출됩니다.

## 예제
여기서는 `EventSource`의 기본 사용 예제를 보여드립니다.

```javascript
// 서버에서 이벤트를 수신하는 EventSource 생성
const eventSource = new EventSource('https://example.com/events');

// 연결이 열릴 때
eventSource.onopen = function(event) {
    console.log('연결이 열렸습니다.', event);
};

// 메시지를 수신할 때
eventSource.onmessage = function(event) {
    console.log('수신된 메시지:', event.data);
};

// 오류가 발생할 때
eventSource.onerror = function(event) {
    console.error('오류 발생:', event);
};
```

## 설명
`EventSource`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **CORS 지원**: 서버는 CORS(Cross-Origin Resource Sharing)를 지원해야 하며, 적절한 헤더를 설정해야 합니다.
2. **HTTPS 사용**: 보안상의 이유로, `EventSource`는 HTTPS 프로토콜을 사용하는 것이 좋습니다.
3. **연결 재시도**: 연결이 끊어지면 브라우저가 자동으로 재연결을 시도합니다. 이는 `onerror` 이벤트에서 확인할 수 있습니다.
4. **데이터 형식**: 서버는 클라이언트가 이해할 수 있는 형식으로 데이터를 전송해야 하며, 기본적으로 텍스트 형식으로 전송됩니다.

## 한 줄 요약
`EventSource`는 JavaScript에서 실시간 서버 전송 이벤트를 통해 지속적으로 데이터를 수신할 수 있도록 지원하는 API입니다.