<!--
Meta Description: # JavaScript의 onerror: 오류 처리 메커니즘 ## 개요 JavaScript의 `onerror`는 웹 페이지에서 발생하는 오류를 감지하고 처리할 수 있는 이벤트 핸들러입니다. 이 기능을 사용하면 스크립트 오류를 효과적으로 처리하고 사용자에게 오류에 대한 ...
Meta Keywords: onerror, error, 오류를, console, 있습니다
-->

# JavaScript의 onerror: 오류 처리 메커니즘

## 개요
JavaScript의 `onerror`는 웹 페이지에서 발생하는 오류를 감지하고 처리할 수 있는 이벤트 핸들러입니다. 이 기능을 사용하면 스크립트 오류를 효과적으로 처리하고 사용자에게 오류에 대한 정보를 제공할 수 있습니다.

## 문서화
### 목적
`onerror`는 주로 JavaScript 코드에서 발생하는 런타임 오류를 감지하는 데 사용됩니다. 이를 통해 개발자는 오류 발생 시 적절한 조치를 취하거나 사용자에게 친숙한 오류 메시지를 표시할 수 있습니다.

### 사용법
`onerror`는 전역 속성으로, 브라우저에서 발생하는 모든 오류를 처리할 수 있습니다. 사용자는 이 속성에 오류 처리 함수를 할당하여 특정 동작을 정의할 수 있습니다.

```javascript
window.onerror = function(message, source, lineno, colno, error) {
    console.log("오류 발생: " + message);
    console.log("소스: " + source);
    console.log("라인 번호: " + lineno);
    console.log("열 번호: " + colno);
    console.log("오류 객체: ", error);
};
```

### 세부 사항
- `message`: 오류 메시지에 대한 문자열입니다.
- `source`: 오류가 발생한 스크립트 파일의 URL입니다.
- `lineno`: 오류가 발생한 라인 번호입니다.
- `colno`: 오류가 발생한 열 번호입니다.
- `error`: 오류 객체로, 추가적인 정보(예: 스택 추적)를 포함할 수 있습니다.

## 예제
### 기본 사용 예제
```javascript
window.onerror = function(message) {
    alert("오류가 발생했습니다: " + message);
};

// 오류를 발생시키는 코드
undefinedFunction(); // 이 함수는 정의되지 않았습니다.
```

### 오류 객체 사용 예제
```javascript
window.onerror = function(message, source, lineno, colno, error) {
    console.error("오류 메시지: ", message);
    console.error("소스: ", source);
    console.error("라인 번호: ", lineno);
    console.error("열 번호: ", colno);
    console.error("오류 객체: ", error);
};

// 발생하는 오류
throw new Error("예외 발생!");
```

## 설명
`onerror`는 여러 오류를 처리할 수 있는 유용한 도구이지만, 몇 가지 주의해야 할 점이 있습니다:

1. **비동기 코드**: `onerror`는 비동기 코드에서 발생하는 오류를 자동으로 잡지 않습니다. 예를 들어, Promise의 `.catch()` 구문을 사용하여 오류를 처리해야 합니다.
   
2. **크로스 도메인 오류**: 외부 스크립트에서 발생한 오류는 보안상의 이유로 `onerror`에서 잡지 않습니다. 이 경우, 오류 메시지에 대한 자세한 정보는 제공되지 않을 수 있습니다.

3. **전역 설정**: `onerror`는 전역적으로 설정되므로, 여러 개의 스크립트에서 오류를 처리할 때 주의해야 합니다.

## 한 줄 요약
JavaScript의 `onerror`는 웹 페이지에서 발생하는 오류를 감지하고 처리하는 이벤트 핸들러입니다.