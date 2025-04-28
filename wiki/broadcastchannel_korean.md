<!--
Meta Description: # BroadcastChannel: JavaScript를 통한 브라우저 간 통신 ## 개요 BroadcastChannel API는 웹 애플리케이션에서 서로 다른 브라우저 탭, 윈도우 또는 프레임 간에 메시지를 비동기적으로 전송할 수 있는 기능을 제공합니다. 이는 데이터...
Meta Keywords: 메시지를, broadcastchannel, 메시지, channel, 동일한
-->

# BroadcastChannel: JavaScript를 통한 브라우저 간 통신

## 개요
BroadcastChannel API는 웹 애플리케이션에서 서로 다른 브라우저 탭, 윈도우 또는 프레임 간에 메시지를 비동기적으로 전송할 수 있는 기능을 제공합니다. 이는 데이터 동기화, 상태 업데이트 및 사용자 인터페이스 변경을 간편하게 관리할 수 있도록 도와줍니다.

## 문서화
### 목적
BroadcastChannel은 여러 문서 간에 메시지를 쉽게 전파할 수 있도록 설계되었습니다. 이는 주로 동일한 출처(origin)를 가진 문서 간에 데이터를 공유하는 데 사용됩니다. 예를 들어, 사용자가 여러 탭에서 동일한 애플리케이션을 열고 있을 때, 한 탭에서 발생한 이벤트를 다른 탭에 전파할 수 있습니다.

### 사용법
BroadcastChannel API를 사용하기 위해서는 먼저 BroadcastChannel 객체를 생성해야 하며, 메시지를 전송하고 수신하는 방법을 정의해야 합니다.

```javascript
// 새로운 BroadcastChannel 생성
const channel = new BroadcastChannel('my_channel');

// 메시지 수신
channel.onmessage = function(event) {
    console.log('수신된 메시지:', event.data);
};

// 메시지 전송
channel.postMessage('안녕하세요, 다른 탭!');
```

### 세부사항
- **Channel 이름**: BroadcastChannel은 생성 시 주어진 이름으로 식별됩니다. 동일한 이름을 가진 모든 채널은 메시지를 공유합니다.
- **메시지 전송**: `postMessage()` 메서드를 사용하여 메시지를 전송합니다. 이 메서드는 비동기적으로 작동하며, 모든 수신 탭에 메시지를 보냅니다.
- **메시지 수신**: `onmessage` 이벤트 리스너를 통해 메시지를 수신합니다. 수신된 메시지는 `event.data` 속성을 통해 접근할 수 있습니다.
- **메모리 관리**: BroadcastChannel을 더 이상 사용하지 않으면 `close()` 메서드를 호출하여 자원을 해제하는 것이 좋습니다.

## 예제
### 기본 사용 예제
```javascript
// 채널 생성
const channel = new BroadcastChannel('test_channel');

// 메시지 수신
channel.onmessage = (event) => {
    console.log('받은 메시지:', event.data);
};

// 다른 탭에 메시지 전송
setTimeout(() => {
    channel.postMessage('안녕하세요, 다른 탭에서!');
}, 1000);
```

## 설명
- **동일한 출처**: BroadcastChannel은 동일한 출처를 가진 문서 간에서만 작동합니다. 즉, 서로 다른 도메인, 프로토콜 또는 포트를 가진 문서 간에는 메시지를 전송할 수 없습니다.
- **성능 고려사항**: 많은 탭이 메시지를 수신할 경우 성능에 영향을 줄 수 있습니다. 따라서 불필요한 메시지 전송을 피하는 것이 좋습니다.
- **브라우저 지원**: BroadcastChannel API는 대부분의 현대 브라우저에서 지원되지만, 사용하기 전에 호환성을 확인하는 것이 중요합니다.

## 한 줄 요약
BroadcastChannel API는 JavaScript를 통해 서로 다른 브라우저 탭 간에 비동기적으로 메시지를 전송할 수 있는 간편한 방법입니다.