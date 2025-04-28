<!--
Meta Description: # Trusted Types: JavaScript의 보안 강화 ## 개요 Trusted Types는 JavaScript에서 XSS(교차 사이트 스크립팅) 공격을 방지하기 위해 도입된 기능입니다. 이를 통해 개발자는 DOM에 삽입되는 잠재적으로 악의적인 문자열을 안전하게...
Meta Keywords: trusted, policy, input, 안전한, const
-->

# Trusted Types: JavaScript의 보안 강화

## 개요
Trusted Types는 JavaScript에서 XSS(교차 사이트 스크립팅) 공격을 방지하기 위해 도입된 기능입니다. 이를 통해 개발자는 DOM에 삽입되는 잠재적으로 악의적인 문자열을 안전하게 관리할 수 있습니다.

## 문서화
Trusted Types의 주 목적은 웹 애플리케이션에서 발생할 수 있는 XSS 공격을 예방하는 것입니다. 이를 위해 개발자는 `Trusted Type` 객체를 생성하고 이를 사용하여 DOM에 삽입할 수 있는 콘텐츠를 제한합니다. Trusted Types는 기본적으로 아래와 같은 절차를 따릅니다:

1. **Trusted Type 생성**: 개발자는 `trustedTypes.createPolicy` 메서드를 사용하여 정책을 정의합니다.
2. **안전한 문자열 반환**: 정의된 정책을 사용하여 신뢰할 수 있는 문자열을 생성합니다.
3. **DOM에 삽입**: 안전하게 생성된 문자열만 DOM에 삽입할 수 있습니다.

### 사용법
```javascript
if (window.trustedTypes) {
    const policy = trustedTypes.createPolicy('my-policy', {
        createHTML: (input) => {
            return input; // 입력 값을 그대로 반환
        },
        createScript: (input) => {
            return input; // 입력 값을 그대로 반환
        }
    });

    const safeHTML = policy.createHTML('<div>안전한 내용</div>');
    document.body.innerHTML = safeHTML; // 안전하게 DOM에 삽입
}
```

## 예시
### 기본 사용 예
```javascript
// Trusted Types 정책 생성
const policy = trustedTypes.createPolicy('example-policy', {
    createHTML: (input) => {
        return input; // 입력된 HTML 반환
    }
});

// 안전한 문자열 생성
const safeHTML = policy.createHTML('<p>안전한 콘텐츠</p>');
document.body.innerHTML = safeHTML; // 콘텐츠 삽입
```

### 스크립트 생성 예
```javascript
const scriptPolicy = trustedTypes.createPolicy('script-policy', {
    createScript: (input) => {
        return input; // 입력된 스크립트 반환
    }
});

// 안전한 스크립트 생성
const safeScript = scriptPolicy.createScript('console.log("안전한 스크립트 실행");');
eval(safeScript); // 스크립트 실행
```

## 설명
Trusted Types를 사용할 때 주의할 점은 다음과 같습니다:

- **정책의 재사용**: 하나의 정책을 여러 곳에서 재사용할 수 있지만, 각 정책은 독립적으로 정의되어야 하며, 각기 다른 보안 요구 사항에 맞게 관리되어야 합니다.
- **정책의 결여**: Trusted Types가 활성화되지 않은 브라우저에서 이 기능을 사용하는 경우, 정책을 정의하지 않으면 기본적으로 모든 문자열이 허용됩니다.
- **CSP와의 통합**: Content Security Policy(CSP)와 함께 사용하면 보안을 더욱 강화할 수 있습니다. 예를 들어, `script-src`와 `object-src`를 제한하여 스크립트의 안전성을 높일 수 있습니다.

## 한 줄 요약
Trusted Types는 JavaScript에서 XSS 공격을 방지하기 위해 신뢰할 수 있는 콘텐츠를 생성하고 관리하는 방법을 제공합니다.