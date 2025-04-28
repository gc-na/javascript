<!--
Meta Description: # ErrorEvent: 자바스크립트에서의 오류 이벤트 처리 ## 개요 `ErrorEvent`는 자바스크립트에서 발생하는 오류에 대한 정보를 제공하는 이벤트 객체입니다. 이 객체는 주로 브라우저에서 웹 페이지의 스크립트 오류를 처리할 때 사용되며, 오류의 세부 정보를 ...
Meta Keywords: errorevent, 발생한, 이벤트, 오류가, event
-->

# ErrorEvent: 자바스크립트에서의 오류 이벤트 처리

## 개요
`ErrorEvent`는 자바스크립트에서 발생하는 오류에 대한 정보를 제공하는 이벤트 객체입니다. 이 객체는 주로 브라우저에서 웹 페이지의 스크립트 오류를 처리할 때 사용되며, 오류의 세부 정보를 수집하고 로그를 기록하는 데 유용합니다.

## 문서화
`ErrorEvent`는 JavaScript에서 오류가 발생할 때 자동으로 생성되는 이벤트입니다. 이 이벤트는 `window.onerror`와 같은 이벤트 핸들러를 통해 처리할 수 있으며, 오류의 원인, 메시지 및 발생한 스크립트의 URL과 같은 정보를 제공합니다.

### 사용법
`ErrorEvent`는 주로 다음과 같이 사용됩니다:

1. **이벤트 리스너 등록**: `window.addEventListener` 메소드를 사용하여 `error` 이벤트에 대한 리스너를 등록합니다.
2. **오류 정보 접근**: 오류가 발생하면 리스너에서 `ErrorEvent` 객체를 통해 오류 메시지, 파일 이름, 행 번호 등을 접근할 수 있습니다.

### 예시 코드
```javascript
// 오류 이벤트 리스너 등록
window.addEventListener('error', function(event) {
    console.log('오류 메시지:', event.message);
    console.log('발생한 스크립트:', event.filename);
    console.log('행 번호:', event.lineno);
    console.log('열 번호:', event.colno);
});

// 의도적으로 오류 발생
undefinedFunction(); // 정의되지 않은 함수 호출로 오류 발생
```

## 설명
`ErrorEvent` 객체는 일반적으로 다음과 같은 속성을 포함합니다:

- `message`: 오류 메시지를 나타냅니다.
- `filename`: 오류가 발생한 스크립트의 파일 이름을 포함합니다.
- `lineno`: 오류가 발생한 행 번호를 나타냅니다.
- `colno`: 오류가 발생한 열 번호를 나타냅니다.
- `error`: 발생한 오류 객체를 포함합니다.

### 일반적인 함정 및 주의사항
- **비동기 코드**: 비동기 함수 내의 오류는 `try-catch` 블록으로 처리되지 않을 수 있습니다. 이 경우 `ErrorEvent`를 통해 오류를 캡처해야 합니다.
- **크로스 도메인 이슈**: 외부 스크립트에서 발생한 오류는 보안 문제로 인해 `filename` 속성이 `null`로 설정될 수 있습니다.
- **브라우저 호환성**: 모든 브라우저가 `ErrorEvent`를 동일하게 지원하지 않을 수 있으므로, 크로스 브라우징을 고려해야 합니다.

## 한 줄 요약
`ErrorEvent`는 자바스크립트에서 발생하는 오류에 대한 정보를 제공하여 오류 처리를 용이하게 합니다.