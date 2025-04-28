<!--
Meta Description: # XMLHttpRequestEventTarget: JavaScript에서의 XMLHttpRequestEventTarget ## 개요 `XMLHttpRequestEventTarget`는 JavaScript의 XMLHttpRequest 객체와 관련된 이벤트를 처리하는 기...
Meta Keywords: xhr, xmlhttprequesteventtarget, console, error, addeventlistener
-->

# XMLHttpRequestEventTarget: JavaScript에서의 XMLHttpRequestEventTarget

## 개요
`XMLHttpRequestEventTarget`는 JavaScript의 XMLHttpRequest 객체와 관련된 이벤트를 처리하는 기능을 제공하는 인터페이스입니다. 이 인터페이스는 XMLHttpRequest의 상태 변화에 대한 이벤트 리스너를 등록하고 관리할 수 있게 해줍니다.

## 문서화
`XMLHttpRequestEventTarget`는 XMLHttpRequest 객체가 네트워크 요청을 수행하는 동안 발생하는 다양한 이벤트에 대한 처리를 가능하게 합니다. 이를 통해 개발자는 요청의 진행 상황을 추적하고, 성공적인 응답, 오류, 또는 요청의 완료 상태를 감지할 수 있습니다.

### 사용 목적
- XMLHttpRequest의 상태 변화에 대한 반응 처리
- 네트워크 요청의 진행 상황을 실시간으로 업데이트
- 요청 성공 여부에 따른 사용자 피드백 제공

### 사용법
`XMLHttpRequestEventTarget`는 다음과 같은 주요 이벤트를 처리할 수 있습니다:
- `load`: 요청이 성공적으로 완료되었을 때 발생
- `error`: 요청 중에 오류가 발생했을 때 발생
- `abort`: 요청이 중단되었을 때 발생
- `progress`: 요청 진행 중에 주기적으로 발생

이벤트 리스너를 등록하는 방법은 다음과 같습니다:

```javascript
const xhr = new XMLHttpRequest();

xhr.addEventListener('load', function() {
    console.log('요청 성공:', xhr.responseText);
});

xhr.addEventListener('error', function() {
    console.error('요청 실패');
});

xhr.addEventListener('abort', function() {
    console.log('요청이 중단되었습니다.');
});

xhr.addEventListener('progress', function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log('진행 상황:', percentComplete + '%');
    }
});

// 요청 설정 및 전송
xhr.open('GET', 'https://api.example.com/data');
xhr.send();
```

## 예제
### 기본 사용 예제
다음은 간단한 XMLHttpRequest를 사용하여 데이터를 요청하는 예제입니다.

```javascript
const xhr = new XMLHttpRequest();

xhr.open('GET', 'https://api.example.com/data', true);

xhr.addEventListener('load', function() {
    if (xhr.status >= 200 && xhr.status < 300) {
        console.log('응답 데이터:', xhr.responseText);
    } else {
        console.error('HTTP 오류:', xhr.status);
    }
});

xhr.addEventListener('error', function() {
    console.error('네트워크 오류 발생');
});

xhr.send();
```

## 설명
`XMLHttpRequestEventTarget`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이벤트 리스너의 중복 등록**: 동일한 이벤트에 대해 여러 번 리스너를 등록하면, 각각의 리스너가 실행됩니다. 필요에 따라 리스너를 제거해야 할 수 있습니다.
  
- **상태 코드 처리**: `load` 이벤트에서 상태 코드(`xhr.status`)를 확인하여 응답이 성공적인지 확인하는 것이 중요합니다.

- **CORS 문제**: 다른 도메인으로 요청을 할 경우 CORS 정책에 따라 요청이 차단될 수 있습니다. 서버에서 CORS 헤더를 적절히 설정해야 합니다.

## 한 줄 요약
`XMLHttpRequestEventTarget`는 JavaScript에서 XMLHttpRequest 요청의 다양한 이벤트를 처리할 수 있는 인터페이스입니다.