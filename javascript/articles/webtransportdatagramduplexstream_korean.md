<!--
Meta Description: # WebTransportDatagramDuplexStream: JavaScript에서의 효율적인 양방향 데이터 전송 ## 개요 `WebTransportDatagramDuplexStream`은 웹 애플리케이션에서 양방향 데이터 전송을 가능하게 하는 JavaScript의...
Meta Keywords: 데이터, webtransportdatagramduplexstream, webtransport, 데이터를, 있습니다
-->

# WebTransportDatagramDuplexStream: JavaScript에서의 효율적인 양방향 데이터 전송

## 개요
`WebTransportDatagramDuplexStream`은 웹 애플리케이션에서 양방향 데이터 전송을 가능하게 하는 JavaScript의 클래스입니다. 이 클래스는 WebTransport API의 일부로, 낮은 지연 시간과 높은 성능을 요구하는 실시간 애플리케이션에 적합합니다.

## 문서화
### 목적
`WebTransportDatagramDuplexStream`는 클라이언트와 서버 간에 데이터그램을 전송할 수 있는 양방향 스트림을 제공합니다. 이를 통해 개발자는 비동기적으로 데이터를 전송하고 수신할 수 있으며, 실시간 애플리케이션에서의 성능을 최적화할 수 있습니다.

### 사용법
`WebTransportDatagramDuplexStream`는 WebTransport 연결을 통해 생성되며, `send()` 메서드로 데이터를 전송하고 `readable.getReader()`를 통해 수신된 데이터를 읽을 수 있습니다. 이 클래스를 사용하기 위해서는 WebTransport API가 지원되는 브라우저에서 실행해야 합니다.

### 세부사항
- **생성**: `WebTransportDatagramDuplexStream`는 WebTransport session이 활성화된 상태에서 생성됩니다.
- **데이터 전송**: `send(data)` 메서드를 호출하여 데이터를 전송합니다.
- **데이터 수신**: `readable` 스트림을 통해 수신된 데이터를 비동기적으로 처리할 수 있습니다.
- **중단 처리**: 스트림이 더 이상 사용되지 않으면, 적절하게 종료해야 합니다.

## 예제
```javascript
// WebTransport 연결 생성
const transport = new WebTransport('wss://example.com/transport');

// 연결이 열리면 스트림 생성
transport.ready.then(() => {
    const duplexStream = transport.datagramDuplexStream;

    // 데이터 전송
    duplexStream.send(new Uint8Array([1, 2, 3]));

    // 데이터 수신
    const reader = duplexStream.readable.getReader();
    reader.read().then(({ done, value }) => {
        if (!done) {
            console.log('수신된 데이터:', value);
        }
    });
});
```

## 설명
`WebTransportDatagramDuplexStream`를 사용할 때 몇 가지 주의할 점이 있습니다:
- **브라우저 호환성**: 현재 `WebTransport` API는 모든 브라우저에서 지원되지 않을 수 있습니다. 최신 브라우저에서 지원 여부를 확인해야 합니다.
- **비동기 처리**: 데이터 전송과 수신은 비동기적이므로, Promise를 적절히 처리해야 합니다.
- **오류 처리**: 네트워크 오류나 스트림 오류에 대한 적절한 예외 처리가 필요합니다.

## 한 줄 요약
`WebTransportDatagramDuplexStream`는 JavaScript에서 실시간 애플리케이션을 위한 양방향 데이터그램 전송을 지원하는 강력한 API입니다.