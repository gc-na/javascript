<!--
Meta Description: # JavaScript의 postMessage: 안전한 데이터 전송 방법 ## 개요 `postMessage`는 서로 다른 출처의 Window 객체 간에 안전하게 데이터를 전송할 수 있는 메서드입니다. 이 메서드는 주로 iframe, 팝업, 또는 다른 창과의 통신에 사용...
Meta Keywords: postmessage, message, 있습니다, 데이터를, 전송할
-->

# JavaScript의 postMessage: 안전한 데이터 전송 방법

## 개요
`postMessage`는 서로 다른 출처의 Window 객체 간에 안전하게 데이터를 전송할 수 있는 메서드입니다. 이 메서드는 주로 iframe, 팝업, 또는 다른 창과의 통신에 사용됩니다.

## 문서화
`postMessage`는 다음과 같은 목적으로 사용됩니다:

- **목적**: 서로 다른 출처의 문서 간에 안전하게 데이터를 전송합니다. 이는 보안상의 이유로 동일 출처 정책(Same-Origin Policy)을 우회할 수 있도록 해줍니다.
  
- **사용법**: 
  - **구문**: `window.postMessage(message, targetOrigin, [transfer]);`
  - **매개변수**:
    - `message`: 전송할 데이터. 문자열 또는 객체(JSON 형식)일 수 있습니다.
    - `targetOrigin`: 메시지를 받을 대상의 출처. 보안을 위해 정확한 출처를 지정해야 합니다.
    - `[transfer]`: 선택적 매개변수로, 전송할 객체의 배열을 지정합니다. 이 객체는 전송 후 더 이상 사용할 수 없습니다.

- **세부사항**: `postMessage`는 비동기적으로 작동하며, 수신자는 `message` 이벤트 리스너를 통해 데이터를 받을 수 있습니다.

## 예제
여기 `postMessage` 사용의 간단한 예시가 있습니다:

### 발신 측
```javascript
// 다른 창이나 iframe에 메시지 전송
const iframe = document.getElementById('myIframe');
iframe.contentWindow.postMessage('안녕하세요, iframe!', 'https://example.com');
```

### 수신 측
```javascript
// 메시지를 수신하는 이벤트 리스너
window.addEventListener('message', function(event) {
    if (event.origin === 'https://example.com') {
        console.log('수신된 메시지:', event.data);
    }
});
```

## 설명
`postMessage`를 사용할 때 주의해야 할 몇 가지 사항은 다음과 같습니다:

- **보안**: `targetOrigin`을 정확히 지정하지 않으면 보안 위험이 발생할 수 있습니다. 모든 출처를 허용하는 '*' 대신, 가능한 한 구체적인 출처를 사용해야 합니다.
  
- **데이터 포맷**: 객체를 전송할 때는 JSON.stringify()를 사용하여 문자열로 변환해야 합니다. 수신 측에서는 JSON.parse()로 다시 객체로 변환할 수 있습니다.

- **이벤트 리스너**: 메시지를 수신하기 위해서는 반드시 `message` 이벤트에 대한 리스너를 설정해야 합니다. 그렇지 않으면 전송된 메시지를 받을 수 없습니다.

## 한 문장 요약
`postMessage`는 서로 다른 출처 간에 안전하게 데이터를 전송하는 JavaScript 메서드입니다.