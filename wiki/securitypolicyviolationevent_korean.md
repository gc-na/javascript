<!--
Meta Description: # SecurityPolicyViolationEvent: JavaScript 보안 정책 위반 이벤트 ## 개요 `SecurityPolicyViolationEvent`는 웹 애플리케이션에서 콘텐츠 보안 정책(CSP) 위반을 감지하기 위해 사용하는 이벤트입니다. 이 이벤트...
Meta Keywords: securitypolicyviolationevent, csp, event, 이벤트는, 사항을
-->

# SecurityPolicyViolationEvent: JavaScript 보안 정책 위반 이벤트

## 개요
`SecurityPolicyViolationEvent`는 웹 애플리케이션에서 콘텐츠 보안 정책(CSP) 위반을 감지하기 위해 사용하는 이벤트입니다. 이 이벤트는 보안 위반 사항을 추적하고 조치를 취하는 데 유용합니다.

## 문서화
`SecurityPolicyViolationEvent`는 주로 CSP가 정의한 규칙을 위반하는 콘텐츠가 로드될 때 발생합니다. 이 이벤트는 웹 페이지에서 보안 위반이 감지되면 발생하며, 개발자는 이를 통해 보안 위반 정보를 수집하고 적절한 대응을 할 수 있습니다.

### 목적
- CSP 위반 사항을 모니터링하고 로깅합니다.
- 보안 위반에 대한 실시간 대응을 가능하게 합니다.

### 사용법
`SecurityPolicyViolationEvent`를 사용하려면, 이벤트 리스너를 추가하여 해당 이벤트를 수신해야 합니다. 이 이벤트는 `window` 객체에서 발생합니다.

```javascript
window.addEventListener('securitypolicyviolation', (event) => {
    console.log('CSP 위반:', event);
});
```

### 세부 사항
- `SecurityPolicyViolationEvent`는 다양한 속성을 가지고 있으며, 이 속성들은 위반의 원인 및 세부 정보를 제공합니다.
  - `blockedURI`: 보안 정책에 의해 차단된 리소스의 URI.
  - `effectiveDirective`: 위반을 발생시킨 CSP 규칙.
  - `originalPolicy`: 적용된 CSP 정책.
  - `sourceFile`: 위반이 발생한 스크립트의 파일 경로.
  - `statusCode`: HTTP 상태 코드.

## 예제
아래는 `SecurityPolicyViolationEvent`의 기본 사용 예시입니다.

```javascript
window.addEventListener('securitypolicyviolation', (event) => {
    console.log('위반된 URI:', event.blockedURI);
    console.log('적용된 지시어:', event.effectiveDirective);
    console.log('원래 정책:', event.originalPolicy);
});
```

이 예제에서는 CSP 위반이 발생했을 때, 차단된 URI 및 정책 정보를 콘솔에 출력합니다.

## 설명
`SecurityPolicyViolationEvent`를 사용할 때 주의할 점은 이벤트가 발생하는 조건을 이해하는 것입니다. 이 이벤트는 브라우저에서 CSP를 지원하는 경우에만 발생합니다. 또한, 모든 CSP 위반이 이 이벤트로 보고되는 것은 아니므로, 보안 정책을 설정할 때 주의가 필요합니다. 

또한, `SecurityPolicyViolationEvent`는 브라우저의 개발자 도구에서 CSP 위반 사항을 추적하는 데에도 유용합니다. 그러나 이 이벤트를 사용하는 것이 보안 위반을 방지하는 것은 아니므로, 항상 CSP 정책을 강력하게 설정하고 주기적으로 검토해야 합니다.

## 한 줄 요약
`SecurityPolicyViolationEvent`는 JavaScript에서 콘텐츠 보안 정책 위반 사항을 감지하고 처리하는 데 사용되는 이벤트입니다.